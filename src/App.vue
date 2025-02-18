<template>
  <div class="page">
    <header class="header">
      <a href="/" class="header__logo">Estate</a>

      <div class="header__menu" :class="{ 'opened': mobiMenuOpened }">
        <div class="header__menu-mobilink" @click="openMobiMenu()"></div>

        <div class="header__menu-content">
          <menu class="header__menu-content-main">
            <template v-for="(item, key) in data.headerMenu">
              <template v-if="key == 0">
                <li class="header__menu-content-main-item" :class="{ 'opened': subMenuOpened }">
                  <span class="header__menu-content-main-item-link _sub" @click="openSubMenu()">{{ item }}</span>

                  <menu class="header__menu-content-main-item-submenu">
                    <a href="" class="header__menu-content-main-item-submenu-item"
                      v-for="subitem in data.headerSubmenu">{{ subitem }}</a>
                  </menu>
                </li>
              </template>

              <template v-else>
                <li class="header__menu-content-main-item">
                  <a class="header__menu-content-main-item-link" href="">{{ item }}</a>
                </li>
              </template>
            </template>
          </menu>

          <div class="header__menu-content-social">
            <a :href="globalVars.tgSrc" class="header__menu-content-social-link"></a>
            <a :href="globalVars.wtspSrc" class="header__menu-content-social-link"></a>
          </div>

          <div class="header__menu-content-tel">
            <a class="header__menu-content-tel-link" :href="'tel:' + globalVars.phoneNum">{{ globalVars.phoneNum }}</a>
            <div class="header__menu-content-tel-mcontent">
              — Москва<br />
              <a class="header__menu-content-tel-link" :href="'tel:' + globalVars.phoneNum2">{{ globalVars.phoneNum2
              }}</a>
              — Владивосток
            </div>
          </div>
        </div>
      </div>

      <div class="header__lang">{{ lang }}</div>
    </header>

    <section class="promo">
      <img class="promo__man" src="./assets/img/bg-promo-man.png" alt="" />
      <div class="promo__main">
        <h3 class="promo__main-title">
          {{ data.promoBlock.title }}
        </h3>

        <div class="promo__main-text">
          {{ data.promoBlock.text }}
        </div>

        <div class="promo__main-footer">
          <a :href="data.promoBlock.btnHref" class="promo__main-footer-btn">{{ data.promoBlock.btnText }}</a>
          <div class="promo__main-footer-socials">
            <a :href="data.promoBlock.linkEdinHref" class="promo__main-footer-socials-one _in"></a>
            <a :href="data.promoBlock.instagrHref" class="promo__main-footer-socials-one _inst"></a>
          </div>
        </div>
      </div>

      <div class="promo__info">
        <div class="promo__info-name">
          {{ data.promoBlock.name }}
        </div>
        <div class="promo__info-state">
          {{ data.promoBlock.state }}
        </div>
      </div>
    </section>

    <SectionBlock :title="data.investTitle" :sectionData="data.investSection" />

    <SectionBlock :title="data.marketingTitle" :sectionData="data.marketingSection" />

    <footer class="footer">
      <div class="footer__left">
        <a href="/" class="footer__left-logo">Estate</a>

        <div class="footer__left-info">
          Москва, БЦ &laquo;Лотос&raquo;, ул. Ленинская, 19<br />
          <a :href="'tel:' + globalVars.phoneNum">{{ globalVars.phoneNum }}</a> — Москва<br />
          <a :href="'tel:' + globalVars.phoneNum2">{{ globalVars.phoneNum2 }}</a> — Владивосток<br />
          <a href="mailTo:hello@estate.ru">hello@estate.ru</a>
        </div>

        <div class="footer__left-social">
          <a class="footer__left-social-link" :href="globalVars.tgSrc"></a>
          <a class="footer__left-social-link" :href="globalVars.wtspSrc"></a>
        </div>
      </div>
      <div class="footer__right">
        <div class="footer__right-links">
          <FooterCol :title="data.footerCol1Title" :links="data.footerCol1Links" />
          <FooterCol :title="data.footerCol2Title" :links="data.footerCol2Links" />
          <FooterCol :title="data.footerCol3Title" :links="data.footerCol3Links" />
        </div>

        <div class="footer__right-copy">
          {{ data.copy }}<br />
          <a href="">{{ data.policy }}</a>
          • <a href="">{{ data.terms }}</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import data from "./data.json";
import SectionBlock from "./components/section.vue";
import FooterCol from "./components/footercol.vue";

export default {
  components: {
    SectionBlock,
    FooterCol
  },
  data() {
    return {
      data: data.ru,
      globalVars: data.globalVars,

      subMenuOpened: false,
      mobiMenuOpened: false,
      lang: "En"
    }
  },
  methods: {
    openSubMenu() {
      this.subMenuOpened = !this.subMenuOpened;
    },
    openMobiMenu() {
      this.mobiMenuOpened = !this.mobiMenuOpened;
    }
  }
}
</script>
<style lang="scss">
@use "@/assets/scss/index.scss";
</style>

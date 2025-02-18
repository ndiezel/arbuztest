<template>
    <section class="section">
        <h2 class="section__title">
            {{ title }}
        </h2>

        <div class="section__blocks">
            <div class="section__blocks-one" v-for="item in sectionData">
                <div class="section__blocks-one-header">
                    <img class="section__blocks-one-header-img" :src="item.imgSrc" :alt="item.name" />
                    <div class="section__blocks-one-header-social">
                        <a v-if="item.instaHref" class="section__blocks-one-header-social-one _inst"
                            :href="item.instaHref" target="_blank"></a>
                        <a v-if="item.linkEdinHref" class="section__blocks-one-header-social-one _linkedin"
                            :href="item.linkEdinHref" target="_blank"></a>
                    </div>
                </div>

                <div class="section__blocks-one-content">
                    <h5 class="section__blocks-one-content-title">
                        {{ item.name }}
                    </h5>
                    <h6 class="section__blocks-one-content-state">
                        {{ item.state }}
                    </h6>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    props: {
        title: String,
        sectionData: Array,
    },
}
</script>
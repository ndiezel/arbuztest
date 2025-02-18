<template>
    <div class="footer__right-links-col">
        <h6 class="footer__right-links-col-title">
            {{ title }}
        </h6>
        <div v-for="item in links">
            <a :href="item.href" class="footer__right-links-col-link">{{ item.text }}</a>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        title: String,
        links: Array,
    },
}
</script>
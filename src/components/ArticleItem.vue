<template>
    <article class="article" :data-id="item.id">
        <div class="article__media">
    
            <img :srcset="require('@/assets/images/'+item.imgMobile) + ' 375w ,' +
                    require('@/assets/images/'+item.imgDesktop) + ' 840w'"
             sizes="(max-width: 1440px) 320px,
                (max-width: 1200px) 1400px"
            :src="require('@/assets/images/'+item.imgMobile)"
            alt="image article">
        </div>
        <div class="article__text">
            <div class="article__nav">
                <span class="article__nav__left"
                @click="emitGoPrev(item.id)">
                    <img :src="require('@/assets/images/icon-angle-left.svg')" alt="icon">
                </span>
                <span class="article__nav__right"
                @click="emitGoNext(item.id)">
                    <img :src="require('@/assets/images/icon-angle-right.svg')" alt="icon">
                </span>
            </div>
            <h3 class="article__title">{{item.title}}</h3>
            <p class="article__description">{{item.description}}</p>
            <div class="article__link">
                <span class="article__link__text">shop now</span>
                <span class="article__link__icon"><img :src="require('@/assets/images/icon-arrow.svg')" alt="image arrow"></span>
            </div>
        </div>
    </article>
</template>

<script>
export default {
    name: 'ArticleItem',
    props: {
        item: {
            type: Object,
            default () {
                return {}
            }
        }
    },
    methods: {
        emitGoPrev(id) {
        this.$emit("emit-go-prev", { message: id });
        },
        emitGoNext(id) {
        this.$emit("emit-go-next", { message: id });
        }
    }
}
</script>


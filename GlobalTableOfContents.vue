<template>
<ul>
    <li v-for="item in items">
        <a :href="item.path">{{item.title || item.path}}</a>
        <ul v-if="item.headers">
            <li v-for="header in item.headers">
                <a :href="item.path + header.slug">{{header.title}}</a>
            </li>
        </ul>
    </li>
</ul>
</template>

<script>
import { resolveSidebarItems } from '@vuepress/theme-default/util/'

export default {
    name: "GlobalTableOfContents",
    computed:{
        items(){
            return resolveSidebarItems(
                this.$page,
                this.$page.regularPath,
                this.$site,
                this.$localePath
            )
        }
    }
}
</script>
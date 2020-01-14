<template>
    <dr-tabs>
        <dr-tab name="Tab'" selected="true">
            TAB1
        </dr-tab>
        <dr-tab name="Tab2">
            <span>TAB2</span>
        </dr-tab>
        <dr-tab name="Tab3">
            <span>TAB3</span>
        </dr-tab>
    </dr-tabs>
</template>

<script>

import DrTabs from './DrTabs'
import DrTab from './DrTab'

export default {

    components:{
        DrTabs,DrTab
    }
}
</script>

<style>

</style>

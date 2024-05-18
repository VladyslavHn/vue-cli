<template>
    <PageContainer>
        <div class="apartments-list">
            <ApartmentsItem v-for="{ id, descr, rating, price } in items" 
            :key="id" 
            :descr="descr" 
            :rating="rating"
            :price="price" 
            class="apartments-list__item" 
            />
        </div>
    </PageContainer>
</template>

<script>

import ApartmentsItem from './ApartmentsItem'
import PageContainer from '../shared/PageContainer'

    export default {
    name: 'ApartmentItem',
    components: {
        ApartmentsItem,
        PageContainer
    },
    props:{
        items: {
            type: Array,
            default: () => []
        }
    }
    }
</script>

<style lang="scss" scoped>
.apartments-list {
    display: flex;
    flex-wrap: wrap;
    margin-left: -15px;
    margin-right: -15px;

    &__item {
        margin-bottom: 30px;
    }
}
</style>
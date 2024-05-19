<template>
    <header class="header">
        <Container>
            <Logo />
        </Container>
    </header>
</template>

<script>
import Container from './shared/PageContainer'
import Logo from './AppLogo'

export default {
    name: 'AppHeader',
    components: {
        Container,
        Logo
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/variables.scss';

.header {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    background: $secondary-color;
    padding: 16px 0;
}
</style>
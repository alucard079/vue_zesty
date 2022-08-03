<template>
    <div class="w-100">
        <b-navbar toggleable="lg" type="dark">
            <b-container fluid>
                <b-navbar-brand href="#">Zesty IO</b-navbar-brand>

            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

            <b-collapse id="nav-collapse" is-nav>
                <b-navbar-nav>
                    <b-nav-item to="/">Home</b-nav-item>
                    <b-nav-item to="/about">About</b-nav-item>
                    <b-nav-item to="/faqs">Faqs</b-nav-item>
                </b-navbar-nav>
            </b-collapse>
            </b-container>
        </b-navbar>
    </div>
</template>

<style>
    .navbar {
        background-color: #1E2329;
    }
    .navbar-brand {
        color: #F6B60D !important;
        font-weight: 700;
    }
    ul.navbar-nav > li.nav-item > a.nav-link { 
        color: #F6B60D; 
        font-weight: 500;
    }
</style>
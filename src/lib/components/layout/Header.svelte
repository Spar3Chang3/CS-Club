<script lang="js">
    import { onMount } from 'svelte';
    import { IconLinks, SiteLinks } from '$lib/index.js';

    let { isMobile = false, prefersDarkMode = true } = $props();

    let navOpen = $state(false);

    function toggleNav(e) {
        e.preventDefault();
        navOpen = !navOpen;
    }

</script>

<style lang="css">

    .header {
        overflow: hidden;
        color: var(--text-standard);
    }

    .fixed-header {
        position: fixed;
        display: grid;
        grid-template-columns: 100%;
        grid-template-rows: 50% 50%;

        min-height: 50px;
        height: 20dvh;
        max-height: 20dvh;
        min-width: 100dvw;
        max-width: 100dvw;

        justify-content: center;
        align-items: center;
    }

    .logo-toggle {
        position: relative;
        display: flex;

        height: 10dvh;
        width: 100%;

        justify-content: end;
        align-items: center;

        background-color: var(--banner-standard);
    }

    .logo {
        height: 100%; /* 10% taken off for wannabe padding */
        width: fit-content;

        margin-right: 2rem;
        object-fit: contain;
    }

    .logo-toggle:hover .logo {
        animation: buzz 0.25s linear infinite;
    }

    .nav-toggle {
        height: 90%;
        width: fit-content;

        border: none;
        background-color: transparent;
        cursor: pointer;

    }

    .navbar {
        height: 10dvh;
        width: 100%;

        background-color: var(--banner-accent);

        visibility: hidden;
        opacity: 0;
        cursor: none;

        transition: all 0.4s ease;
    }

    .navbar-visible {
        visibility: visible;
        opacity: 1;
        cursor: auto;
    }

    .nav-menu {
        position: relative;
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(80px, 1fr));

        height: 100%;
        width: 100%;

        justify-content: center;
        align-items: center;

        list-style: none;
        margin: 0;
        padding: 0;
    }

    .nav-menu li {
        height: 100%;
        width: 100%;
    }

    .nav-menu a {
        display: flex;

        height: inherit;
        width: inherit;

        justify-content: center;
        align-items: center;

        text-decoration: none;
        font-size: 2rem;
        color: var(--text-standard);
    }

    .nav-menu a:hover {
        animation: buzz 0.1s linear infinite;
    }

    .relative-header {
        height: 10dvh;
    }

    @keyframes buzz {
        0%, 100% {
            transform: translate(0, 0) rotate(0deg);
        }
        25% {
            transform: translate(-2px, -2px) rotate(-2deg);
        }
        50% {
            transform: translate(2px, 2px) rotate(2deg);
        }
        75% {
            transform: translate(-2px, 2px) rotate(-2deg);
        }
    }


</style>
<!--<svg xmlns="http://www.w3.org/2000/svg" width="400" height="346.4" viewBox="0 0 400 346.4">
    <g fill-rule="evenodd">
        <path id="power" d="M195.101 33.651 195.2 63.2h8.8V12.8h-8.8V38m18.104-6.6c-1.131 4.22-.543 5.738 3.121 8.06 19.65 12.451 16.264 44.061-5.628 52.535-32.385 12.535-56.243-30.422-28.779-51.818 3.226-2.513 4.347-7.333 2.262-9.72-.65-.744-5.691 2.321-9.595 5.835-25.363 22.826-9.267 65.308 24.745 65.308 38.278 0 52.192-50.681 19.161-69.793-4.592-2.657-4.682-2.664-5.287-.407" fill="#F0F"/>
    </g>
</svg> This is the SVG for the power button. I imagine if we just put them in the exact same spot, they'll overlay nicely with like an absolute position. Maybe not. Please feel free to delete, for I am not competent I'd also like a glow effect applied to the power button when selected.-->
<section class="header">
    <div class="fixed-header">
        <div class="logo-toggle">
            <button class="nav-toggle" onclick={toggleNav}>
                <img class="logo" src={prefersDarkMode ? IconLinks.CSClub.light : IconLinks.CSClub.dark} alt="Computer Science Club Logo"/>

            </button>
        </div>
        <nav class="navbar" class:navbar-visible={navOpen}>
            <ul class="nav-menu">
                <li><a href={SiteLinks.about}>About Us</a></li>
                <li><a href={SiteLinks.staff}>Staff</a></li>
            </ul>
        </nav>
    </div>
    <div class="relative-header">

    </div>
</section>
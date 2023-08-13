<style>

    * {
        font-family: "Outfit", Sans-serif;
        color: #9a9a9a;
        font-weight: 400;
    }

    .background {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: -1;
    }

    .about-me-wrap {
        width: 100vw;
        height: 100vh;

        display: flex;

        align-items: center;
        justify-content: center;
    }

    .about-me {
        background-color: #141414;

        outline-color: #1f1f1f;
        outline-width: 3px;
        outline-style: solid;

        width: 450px;
        height: 615px;

        display: flex;
        flex-direction: column;

        align-items: center;
    }



    .profile-picture {
        margin-top: 56px;

        width: 130px;
        height: 130px;

        border-radius: 50%;
    }

    .name {
        margin-top: 10px;

        width: 75%;
        height: auto;

        font-family: "Outfit", Sans-serif;
        font-size: 42px;
        text-align: center;
    }

    .info {
        margin-top: 10px;

        width: 75%;
        height: auto;
        font-size: 18px;
        
        text-align: center;
    }

    .check-it-out {
        margin-top: auto;
        margin-bottom: 30px;

        font-family: "Outfit", Sans-serif;
        font-size: 18px;

        background: none;
        border: none;

        padding: 10px;

        cursor: pointer;
        animation: transform 0.3s ease-in-out forwards;
    }

    @keyframes shift-up {
        0% {
            transform: translateY(0px);
        }

        100% {
            transform: translateY(-5px);
        }
    }
    @keyframes shift-down {
        0% {
            transform: translateY(-5px);
        }

        100% {
            transform: translateY(0px);
        }
    }

    .check-it-out:hover {
        animation-name: shift-up;
    }
    .check-it-out:not(:hover) {
        animation-name: shift-down;
    }

    .arrow {
        transform: translateY(3px);
        width: 20px;
        height: 20px;
    }

    .links {
        margin-top: 10px;

        display: flex;
        gap: 10px;
        flex-direction: row;

        align-items: center;
        justify-content: center;

        width: 75%;
        height: 50px;
    }

    .link-icon {
        width: 30px;
        height: 30px;

        transition: filter 0.3s ease-in-out;
        filter: brightness(1)
    }

    .link-icon:hover {
        animation: brighten 0.3s ease-in-out forwards;
        filter: brightness(2)
    }

    .projects {
        padding-bottom: 500px;
        padding-top: 50px;

        width: 100vw;
        min-height: 60vh;
        height: auto;

        border-top: 3px #274f7a solid;
        background-color: #161616;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        row-gap: 50px;
    }

    .project {
        width: 60%;

        margin-top: 0px;

        min-height: 650px;
        height: auto;
        overflow: hidden;
    }

    .project-title {
        padding-top: 15px;
        padding-bottom: 15px;

        border-bottom: 3px solid #242424;

        font-family: "Outfit", Sans-serif;
        font-size: 42px;

        display: flex;
        /* border: 1px solid red; */

    }

    .project-link {
        width: 40px;
        height: 40px;

        transform: translateY(13px) rotate(-135deg);
        margin-left: auto;
    }

    .project-link img {
        width: 100%;
        height: 100%;
    }

    .project-desc {
        padding-top: 15px;
        padding-bottom: 15px;

        font-family: "Outfit", Sans-serif;
        font-size: 18px;
        height: auto;
    }

    .project-desc p {
        margin-bottom: 20px;
    }

    .icons-container {
        width: 100%;
        height: 23px;

        display: flex;
        flex-direction: row;
        gap: 10px;
    }

    .devicon  {
        width: 100%;
        height: 100%;

        /* display: contents; */
        font-size: 35px;
        outline: none;

        display: inline-block;

        transition: color 0.3s ease-in-out;
    }

    /* .colored {
        transition: color 0.3s ease-in-out;
    } */

    .project-images {
        margin-top: 40px;
        padding-bottom: 10px;

        display: flex;
        flex-direction: row;
        align-items: center;

        overflow-x: scroll;
        overflow-y: hidden;

        gap: 20px;
        height: 375px;
    }

    .project-image-wrap {
        width: auto;
        height: 100%;
    }

    .project-image {
        border: 2px solid #242424;
        border-radius: 5px;

        height: 100%;
        max-width: 600px;

        object-fit: cover;
        object-position: left;

        cursor: pointer;
    }

    .image-background {
        width: 100vw;
        height: 100vh;

        background-color: black;

        opacity: 50%;
        
        position: fixed;
        z-index: -1;
    }

    .image-wrapper {
        width: 100vw;
        height: 100vh;

        display: flex;
        justify-content: center;
        align-items: center;

        z-index: 5;
        position: fixed;

        /* transition: opacity 0.2s ease-in-out; */;
    }

    .image-container {
        width: 60%;
        height: 60%;
    }

    .image {
        width: 100%;
        height: 100%;

        object-fit: contain;
    }


</style>

<link rel="stylesheet" href="src\styles\fullPhoto.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css">

<script>
    import name from './name.svelte';

    import { quintInOut, quintOut } from 'svelte/easing';
    import { fade } from 'svelte/transition';

    let projectsDiv;

    function scrollToProjects() {
        if (!projectsDiv) return;
        projectsDiv.scrollIntoView({ behavior: 'smooth' });
    }

    let projects = {
        "Chess Bot": {
            "Desc": "A Chess bot created using a combination of Selenium and Stockfish.",
            "Link": "https://github.com/Sw1ndlerScripts/ChessBot",
            "Icons": {
                "python": "https://www.python.org/",
                "selenium": "https://www.selenium.dev/",
            },
            "Images": ['ChessBot/chess1.png', 'ChessBot/chess2.png', 'ChessBot/chess3.png', 'ChessBot/chess4.png', 'ChessBot/chess5.png' ]
        },
        "Portfolio": {
            "Desc": "A Portfolio website I created for my projects, you're looking at it right now\nIt uses svelte and is able to dynamically add projects from json",
            "Link": "https://github.com/Sw1ndlerScripts/Portfolio",
            "Icons": {
                "html5": "https://www.w3schools.com/html/",
                "css3": "https://www.w3schools.com/css/",
                "javascript": "https://www.javascript.com/",
                "svelte": "https://svelte.dev/",
            },
            "Images": ['Portfolio/portfolio1.png', 'Portfolio/portfolio2.png']
        },
        "Calculator": {
            "Desc": "A simple calculator I made using svelte in 20 minutes",
            "Link": "https://sw1ndler.tk/calculator/",
            "Icons": {
                "html5": "https://www.w3schools.com/html/",
                "css3": "https://www.w3schools.com/css/",
                "javascript": "https://www.javascript.com/",
                "svelte": "https://svelte.dev/",
            },
            "Images": ['Calculator/calculator1.png', 'Calculator/calculator2.png']
        },
        "Scripts": {
            "Desc": "A collection of roblox scripts I've made",
            "Link": "https://github.com/Sw1ndlerScripts/RobloxScripts",
            "Icons": {
                "lua": "https://www.lua.org/",
            },
            "Images": []
        }
    };

    let visible = false;
    let imgSource = "sample.png"

    function fadeImage() {
        visible = !visible;
    }

    function showImage(event) {
        imgSource = event.target.src;
        visible = true;
    }

    function horizontalScroll(event) {
        const scrollContainer = event.currentTarget;

        const { scrollLeft, scrollWidth, clientWidth } = scrollContainer;

        // const isAtEnd = scrollLeft + clientWidth >= scrollWidth;
        // if (isAtEnd && event.deltaY > 0) { return; }

        event.preventDefault();
        // scrollContainer.scrollLeft += event.deltaY;

        let i = 0;
        while (i <= 50) {
            i++
            setTimeout(() => {
                scrollContainer.scrollLeft += (event.deltaY / 50);
            }, 5 * i)
        }
    }

    let hoveredIcon = ""

    function iconMouseEnter(iconName) {
        hoveredIcon = iconName;
    }
    function iconMouseLeave() {
        hoveredIcon = "";
    }

</script>


{#if visible}
    <div class='image-wrapper' on:click={fadeImage} on:keydown={fadeImage} transition:fade={{ duration: 300, easing: quintInOut}}>
        <div class='image-background'></div>

        <div class='image-container'>
            <img class='image' alt='' src={imgSource} />
        </div>
    </div>
{/if}



<img class='background' src="/background.svg" alt='background'>

<div class='about-me-wrap'>
    <div class='about-me'>
        <img class="profile-picture" src='/pfp.png' alt='pfp'>
        
        <div class='name'>
            Hi <br> I'm Sw1ndler
        </div>

        <div class='info'>
            Life Is Roblox
        </div>

        <div class='links'>
            <a href='https://github.com/Sw1ndlerScripts' target="_blank"> <img class='link-icon' src='Icons/github.svg' alt='github'> </a>
            <a href='https://discord.com/users/425797455486124032' target="_blank"> <img class='link-icon' src='Icons/discord.svg' alt='discord'> </a>
        </div>
    
        <button class='check-it-out' on:click={scrollToProjects}>
            Check it out <img src="Icons/arrow.svg" alt='down_arrow' class='arrow'>
        </button>
    </div>
</div>

<div class='projects' id='projects' bind:this={projectsDiv}>
    {#each Object.entries(projects) as [projectName, project]}
        <div class='project'>
            <div class='project-title'>
                {projectName} <a href={project['Link']} class='project-link' target="_blank"> <img src="Icons/arrow.svg" alt='project-link'> </a>
            </div>

            <div class='project-desc'>
                {#each project["Desc"].split('\n') as line}
                    <p>{line}</p>
                {/each}


                <div class='icons-container'>
                    {#each Object.entries(project["Icons"]) as [iconName, link]}
                        <a 
                            class="project-icon" 
                            href={link} 
                            target="_blank"
                            on:mouseenter={() => iconMouseEnter(iconName)}
                            on:mouseleave={iconMouseLeave}
                        >
                            <i 
                            class={hoveredIcon === iconName ? `devicon-${iconName}-plain devicon colored` : `devicon-${iconName}-plain devicon`}
                            ></i>
                        </a>
                    {/each}
                </div>

                <div class='project-images' on:wheel={horizontalScroll}>
                    {#each project["Images"] as image}
                        <div class='project-image-wrap'>
                            <img class="project-image" src="Projects/{image}" alt='1' on:click={showImage} on:keydown={showImage}> 
                        </div>
                    {/each}
                </div>
            </div>
        </div>
    {/each}
</div>
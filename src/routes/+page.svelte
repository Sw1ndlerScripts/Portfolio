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

        animation-duration: 0.3s;
        animation-timing-function: ease-in-out;
        animation-fill-mode: forwards;
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
    }

    .projects {
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
    }

    .project {
        width: 60%;

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
        width: 40px;
        height: 40px;
    }
    
    .project-desc {
        padding-top: 15px;
        padding-bottom: 15px;

        font-family: "Outfit", Sans-serif;
        font-size: 18px;
        height: auto;
    }

    .project-images {
        margin-top: 30px;

        display: flex;
        flex-direction: row;
        align-items: center;

        overflow-x: scroll;
        overflow-y: hidden;
        

        gap: 38px;
        height: 375px;
    }

    .project-image {
        border: 1px solid #242424;

        width: 400px;

        height: 100%;
        max-width: 25%;

        object-fit: cover;
        object-position: left;
    }

    /* * {
        border: 1px solid red;
    } */



</style>

<link rel="stylesheet" href="src\styles\fullPhoto.css">

<script>
    import { quintInOut, quintOut } from 'svelte/easing';
    import { crossfade } from 'svelte/transition';
    import { fade } from 'svelte/transition';

    function scrollToProjects() {
        const projectsDiv = document.getElementById('projects');
        if (!projectsDiv) return;
        projectsDiv.scrollIntoView({ behavior: 'smooth' });
    }

    let projects = {
        "Chess Bot": {
            "Desc": "A Chess bot created using a combination of Selenium and Stockfish.",
            "Link": "https://github.com/Sw1ndlerScripts/ChessBot",
            "Images": ['/ChessBot/chess1.png', '/ChessBot/chess2.png', '/ChessBot/chess3.png', '/ChessBot/chess4.png', '/ChessBot/chess5.png' ]
        },
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
            ( I Code Things )
        </div>

        <div class='links'>
            <a href='https://github.com/Sw1ndlerScripts' target="_blank"> <img class='link-icon' src='/icons/github.svg' alt='github'> </a>
            <a href='https://discord.com/users/425797455486124032' target="_blank"> <img class='link-icon' src='/icons/discord.svg' alt='discord'> </a>

        </div>
    
        <button class='check-it-out' on:click={scrollToProjects}>
            Check it out <img src="/icons/arrow.svg" alt='down_arrow' class='arrow'>
        </button>
    </div>
</div>

<div class='projects' id='projects'>
    {#each Object.entries(projects) as [projectName, project]}
    
        <div class='project'>
            <div class='project-title'>
                {projectName} <a href={project['Link']} class='project-link' target="_blank"> <img src="/icons/arrow.svg" alt='project-link'> </a>
            </div>

            <div class='project-desc'>
                {project["Desc"]}

                <div class='project-images'>
                    {#each project["Images"] as image}
                        <img class="project-image" src="Projects/{image}" alt='1' on:click={showImage} on:keydown={showImage}> 
                    {/each}
                </div>

            </div>
        </div>

    {/each}
</div>
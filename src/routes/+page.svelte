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
        outline-width: 5px;
        outline-style: solid;

        width: 600px;
        height: 820px;

        display: flex;
        flex-direction: column;

        align-items: center;
    }



    .profile-picture {
        margin-top: 75px;

        width: 175px;
        height: 175px;

        border-radius: 50%;
    }

    .name {
        margin-top: 15px;

        width: 75%;
        height: auto;

        font-family: "Outfit", Sans-serif;
        font-size: 56px;
        text-align: center;
    }

    .info {
        margin-top: 15px;

        width: 75%;
        height: auto;
        font-size: 25px;
        
        text-align: center;
    }

    .check-it-out {
        margin-top: auto;
        margin-bottom: 50px;

        font-family: "Outfit", Sans-serif;
        font-size: 25px;

        

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
    }

    .links {
        margin-top: 15px;

        display: flex;
        gap: 10px;
        flex-direction: row;

        align-items: center;
        justify-content: center;

        width: 75%;
        height: 50px;
    }

    .link-icon {
        width: 40px;
        height: 40px;
    }

    .projects {
        padding-top: 50px;

        width: 100vw;
        height: 100vh;

        border-top: 5px #274f7a solid;
        background-color: #161616;

        display: flex;
        justify-content: center;
    }

    .project {
        width: 60vw;
        height: 1000px;


        /* border-top: 5px #242424 solid;
        border-bottom: 5px #242424 solid;

        background-color: #1a1a1a; */
    }

    .project-title {
        padding-top: 15px;
        padding-bottom: 15px;

        border-bottom: 3px solid #242424;

        font-family: "Outfit", Sans-serif;
        font-size: 56px;

        /* border: 1px solid red; */

    }

    .project-desc {
        padding-top: 15px;
        padding-bottom: 15px;

        font-family: "Outfit", Sans-serif;
        font-size: 25px;
        height: auto;
    }

    .project-images {

        margin-top: 30px;

        display: flex;
        flex-direction: row;
        align-items: center;

        gap: 50px;
        height: 500px;
    }

    .project-image {
        border: 1px solid #242424;

        width: 400px;
        height: 100%;

        object-fit: cover;
        
        
    }

    /* * {
        border: 1px solid red;
    } */


</style>

<script>
    function scrollToProjects() {
        const projectsDiv = document.getElementById('projects');
        if (!projectsDiv) return;
        projectsDiv.scrollIntoView({ behavior: 'smooth' });
    }

    function test() {
        alert("test")
    }

    let projects = {
        "Chess Bot": {
            "Desc": "A Chess bot created using a combination of Selenium and Stockfish.",
            "Images": ['sample.png', 'sample2.png', 'sample3.png']
        }
    };


</script>


<div class='about-me-wrap'>
    <img class='background' src="/background.svg" alt='background'>

    <div class='about-me'>
        <img class="profile-picture" src='/pfp.png' alt='pfp'>
        
        <div class='name'>
            Hi <br> I'm Sw1ndler
        </div>

        <div class='info'>
            ( I Code Things )
        </div>

        <div class='links'>
            <a href='https://github.com/Sw1ndlerScripts'> <img class='link-icon' src='/icons/github.svg' alt='github'> </a>
            <a href='https://discord.com/users/425797455486124032'> <img class='link-icon' src='/icons/discord.svg' alt='discord'> </a>

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
                {projectName}
            </div>

            <div class='project-desc'>

                {project["Desc"]}

                <div class='project-images'>
                    {#each project["Images"] as image}
                        <img class="project-image" src="/{image}" alt='1'> 
                    {/each}
                </div>
            </div>
        </div>

    {/each}
</div>
<template>
    <div class="wrapper">
        <div class="about container draggable" :style="{ top: position.y + 'px', left: position.x + 'px' }"
            @mousedown="startDrag" @mousemove="handleDrag" @mouseup="stopDrag">
            <p>
                Hello! I'm Hossam El_Deen, FullStack with a knack for crafting elegant and user-friendly
                interfaces.
                With a background in computer science and a love for coding, I bring creativity and attention to detail
                to every
                project.
                <a href="https://github.com/HossamElDeenKamal2003" target="_blank">GitHub</a>
            </p>
            <h2>Skills</h2>
            <ul>
                <li>HTML5, CSS3, JavaScript (ES6+)</li>
                <li>React.js, Vue.js, </li>
                <li>Nodejs, </li>
                <li>Responsive Web Design, </li>
                <li>UI/UX Design Principles, </li>
                <li>C++, </li>
                <li>C#, </li>
                <li>OOP, </li>
                <li>Problem Solver</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'articleAbout',
    data() {
        return {
            isDragging: false,
            position: { x: 0, y: 0 },
            offset: { x: 0, y: 0 },
        };
    },
    methods: {
        startDrag(event) {
            this.isDragging = true;
            this.offset = {
                x: event.clientX - this.position.x,
                y: event.clientY - this.position.y,
            };
        },
        handleDrag(event) {
            if (this.isDragging) {
                this.position = {
                    x: event.clientX - this.offset.x,
                    y: event.clientY - this.offset.y,
                };
            }
        },
        stopDrag() {
            this.isDragging = false;
        },
    },
}
</script>

<style scoped>
.wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    padding: 1em;
    box-sizing: border-box;
    position: relative;
}

.about {
    margin-top: 0em;
    text-align: center;
    padding: 1em;
    max-width: 600px;
    width: 100%;
    box-sizing: border-box;
    border: 1px solid #ccc;
    border-radius: 10px;
    background-color: #f9f9f9;
}

.draggable:active {
    cursor: grabbing;
}

p,
h2,
li {
    font-size: 1.2em;
    background: linear-gradient(45deg, #4CAF50, #FFC107);
    -webkit-background-clip: text;
    /* Vendor-prefixed version for WebKit browsers */
    background-clip: text;
    color: transparent;
    display: inline-block;
    animation-name: desani;
    animation-duration: 2s;
    animation-timing-function: ease-out;
    animation-fill-mode: forwards;
    font-family: 'Times New Roman', Times, serif;
}

@keyframes desani {
    0% {
        opacity: 0;
        transform: translateY(0);
    }

    100% {
        opacity: 1;
        transform: translateY(0);
    }
}

ul {
    list-style: none;
    animation: fadeInUp 1s ease-out forwards;
}

@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(20px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Media queries for responsiveness */
@media (max-width: 600px) {
    p,
    h2,
    li {
        font-size: 1em;
    }
}
</style>

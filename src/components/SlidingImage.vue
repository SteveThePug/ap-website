<template>
    <div v-for="(imageSrc, index) in        imageSources       " :key="imageSrc">
        <img :src="imageSrc" :style="getImageStyle(index)" alt=" Image" />
    </div>
</template>
<style scoped>
img {
    width: 40vh;
    height: 40vh;
    position: absolute;
    transition: top 5s linear, left 5s ease, opacity 3s ease;
}
</style>
<script>

export default {
    data() {
        let sources = [];
        for (let i = 1; i < 22; i++) {
            sources.push(`src/assets/img/${i}.jpg`)
        }

        let positions = [];
        for (let i = 0; i < 21; i++) {
            positions.push({ top: `${50 + (Math.random() - 0.5) * 10}vh`, left: `100vw` });
        }

        return {
            imageSources: sources,
            imagePositions: positions,
        };
    },
    mounted() {
        //GSAP for animation
        //CSS transition events
        //NUXT3
        // Lottie


        this.imagePositions.forEach((position, index) => {
            setTimeout(() => {
                this.imagePositions[index] = { top: `${5 + Math.random() * 30}vh`, left: `-50vh` };
                setTimeout(() => {
                    this.imagePositions[index] = { top: `${5 + Math.random() * 30}vh`, left: `100vw` };
                }, 5000);
            }, index * 500); // Adjust the delay as needed
        })

        setInterval(() => {
            this.imagePositions.forEach((position, index) => {
                setTimeout(() => {
                    this.imagePositions[index] = { top: `${5 + Math.random() * 30}vh`, left: `-50vh` };
                    setTimeout(() => {
                        this.imagePositions[index] = { top: `${5 + Math.random() * 30}vh`, left: `100vw` };
                    }, 5000);
                }, index * 500); // Adjust the delay as needed
            });

        }, this.imagePositions.length * 500)
    },
    methods: {
        getImageStyle(index) {
            const position = this.imagePositions[index] || {}; // Get position for the image
            return {
                position: "absolute",
                top: position.top || "0",
                left: position.left || "0"

            };
        }
    }
}
</script>
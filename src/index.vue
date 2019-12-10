<template>
    <div style="display: flex">
        <div class="slider"></div>
        <div class="main"></div>
    </div>
</template>

<script>
    import zrender from 'zrender';

    export default {
        name: "index",
        data() {
            return {
                main: null,
                slider: null,
                Isogon: null,
            };
        },
        mounted() {
            this.slider = zrender.init(document.querySelector('.slider'));
            this.main = zrender.init(document.querySelector('.main'));
            this.init();
        },
        methods: {
            init() {
                let list = {
                    Isogon: () => {
                        this.slider.add(
                            new zrender.Isogon({
                                shape: {
                                    x: 75,
                                    y: 75,
                                    r: 40,
                                    n: 4
                                },
                                style: {
                                    fill: 'white',
                                    stroke: '#F00'
                                },
                            }).on('click', () => {
                                this.createNew('Isogon');
                            })
                        );
                    },
                    Rect: () => {
                        this.slider.add(
                            new zrender.Rect({
                                shape: {
                                    x: 35,
                                    y: 150,
                                    r: [1],
                                    width: 80,
                                    height: 80
                                },
                                style: {
                                    fill: 'white',
                                    stroke: '#F00'
                                },
                            }).on('click', () => {
                                this.createNew('Rect');
                            })
                        );
                    }
                };
                Object.keys(list).forEach(key => {
                    list[key]();
                });
            },
            createNew(name) {
                let list = {
                    Isogon: () => {
                        this.main.add(new zrender.Isogon({
                            shape: {
                                x: 75,
                                y: 75,
                                r: 40,
                                n: 4
                            },
                            style: {
                                fill: 'white',
                                stroke: '#F00'
                            },
                            draggable: true
                        }));

                    },
                    Rect: () => {
                        this.main.add(
                            new zrender.Rect({
                                shape: {
                                    x: 35,
                                    y: 150,
                                    r: [1],
                                    width: 80,
                                    height: 80
                                },
                                style: {
                                    fill: 'white',
                                    stroke: '#F00'
                                },
                                draggable: true
                            })
                        );
                    }
                };
                list[name]();
            },
        }
    };
</script>

<style scoped>
    * {
        margin: 0;
        padding: 0
    }

    .slider {
        height: 100vh;
        width: 20vw;
        border-right: 1px solid;
    }

    .main {
        height: 100vh;
        width: 80vw;
    }

</style>

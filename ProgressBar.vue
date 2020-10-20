<template>
    <div>
        {{ title }}
        <div class="progress">
            <div class="progress-bar" :class="classes" :style="`${customStyle} width: ${newPercentage}%;`" aria-valuemax="100"></div>
        </div>
    </div>
</template>
<script>
export default {
    name: "ProgressBar",
    props: {
        title: {type: String},
        percentage: {type: Number, default: 100},
        delay: {type: Number, default: 0},
        bg: {type: String, default: 'primary'},
        customBgColor: {type: String, default:null},
        animation: {type: Boolean, default: false},
        striped: {type: Boolean, default: false},
    },
    data() {
        return{
            newPercentage: 0,
            classes: null,
            customStyle: ""
        }
    },
    created() {
        this.classes = 'bg-' + this.bg
        if(this.customBgColor!=null){this.customStyle = ` background-color:${this.customBgColor}!important;`}

        if(this.animation){this.classes = this.classes +  " progress-bar-animated"}
        if(this.striped){this.classes = this.classes +  " progress-bar-striped"}
        setTimeout(() => {
            this.newPercentage = this.percentage
        }, this.delay);
    }
}
</script>

<style scoped>
    .progress{display:-webkit-box;display:-ms-flexbox;display:flex;height:1rem;overflow:hidden;font-size:.75rem;background-color:#e9ecef;border-radius:.25rem;margin:5px 0 10px}
    .progress-bar{display:-webkit-box;display:-ms-flexbox;display:flex;-webkit-box-orient:vertical;-webkit-box-direction:normal;-ms-flex-direction:column;flex-direction:column;-webkit-box-pack:center;-ms-flex-pack:center;justify-content:center;color:#fff;text-align:center;background-color:#007bff;transition:width .6s ease}
    .progress-bar-striped{background-image:linear-gradient(45deg,rgba(255,255,255,.15) 25%,transparent 25%,transparent 50%,rgba(255,255,255,.15) 50%,rgba(255,255,255,.15) 75%,transparent 75%,transparent);background-size:1rem 1rem}
    .progress-bar-animated{-webkit-animation:progress-bar-stripes 1s linear infinite;animation:progress-bar-stripes 1s linear infinite}
    @-webkit-keyframes progress-bar-stripes {
        from{background-position:1rem 0}
        to{background-position:0 0}
    }
    @keyframes progress-bar-stripes {
        from{background-position:1rem 0}
        to{background-position:0 0}
    }
    .bg-success{background-color:#28a745!important}
    .bg-secondary{background-color:#6c757d!important}
    .bg-info{background-color:#17a2b8!important}
    .bg-danger{background-color:#dc3545!important}
    .bg-warning{background-color:#ffc107!important}
    .bg-turquoise{background-color:#1abc9c!important}
    .bg-amethyst{background-color:#9b59b6!important}
    .bg-midnightblue{background-color:#2c3e50!important}
    .bg-electronblue{background-color:#0984e3!important}
    .bg-shymoment{background-color:#a29bfe!important}
    .bg-pinkglamour{background-color:#ff7675!important}
    .bg-brightyarrow{background-color:#fdcb6e!important}
    .bg-americanriver{background-color:#636e72!important}
    .bg-picopink{background-color:#fd79a8!important}
    .bg-pink{background-color:pink!important}
    .bg-exodusfruit{background-color:#686de0!important}
    .bg-pureapple{background-color:#6ab04c!important}
</style>
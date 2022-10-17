<script>
export default {
  functional: true,
  props: {
    img: {
      type: String,
      default:
        'https://avatars1.githubusercontent.com/u/47616551?s=460&u=f9f81df034252d349d5c631a85cd57ea603beefa&v=4',
    },
    circle: [Boolean, String],
    size: {
      type: String
    },
  },
  render(h, context) {
    const { props } = context
    // console.log(props)
    return h(
      'img',
      {
        class: {
          circular: props.circle, //deixar perfil redondo
          sm: props.size === 'sm',
        },
        attrs: {
          src: props.img,
          alt: 'avatar',
        },
      },
      []
    )
  },
}
</script>
<style scoped>
.circular {
  border-radius: 50%;
}
.sm {
  height: 80px;
  float: left;
  padding: 0 10px;
}
/* .md {
  height: 150px;
}
.lg {
  height: 300px;
} */
</style>

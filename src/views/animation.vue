<script lang="ts">
export default {
  data() {
    return {
      isAddItemVisible: false,
    }
  },
  mounted() {
    // You can trigger the animation when the component is mounted or based on some other event
    this.showAddItem()
  },
  methods: {
    showAddItem() {
      this.isAddItemVisible = true
    },
  },
}
</script>

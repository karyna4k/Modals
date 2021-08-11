<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">
            Show first modal
          </button>

          <!-- first modal -->
          <Modal
            title="First modal"
            v-show="modalFirst"
            @close="modalFirst = !modalFirst"
          >
            <div slot="body">
              <p>
                Lorem ipsum, dolor sit amet consectetur adipisicing elit.
                Reiciendis eos quibusdam tenetur illum perspiciatis numquam
                atque delectus dolorum minima facere assumenda, soluta debitis
                voluptas deserunt eligendi quod fugit ullam aliquid.
              </p>
              <button class="btn btnPrimary" @click="modalFirst = !modalFirst">
                Well done!
              </button>
            </div>
          </Modal>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import Modal from "@/components/Modal.vue";

export default {
  components: { Modal },
  data() {
    return {
      modalFirst: false,
    };
  },
};
</script>

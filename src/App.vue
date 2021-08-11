<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <!-- first modal -->
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">
            Show first modal
          </button>

          <Modal
            title="First modal"
            v-show="modalFirst"
            @close="modalFirst = false"
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

          <!-- second modal -->
          <button
            class="btn btnPrimary"
            @click="secondModal.show = !secondModal.show"
          >
            Show modal with form
          </button>

          <Modal
            title="Modal with form"
            v-show="secondModal.show"
            @close="secondModal.show = false"
          >
            <div slot="body">
              <form @submit.prevent="submitSecondForm">
                <label>Name:</label>
                <input v-model="secondModal.name" required type="text" />
                <label>Email:</label>
                <input v-model="secondModal.email" required type="email" />
                <button class="btn btnPrimary">Submit!</button>
              </form>
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
      secondModal: {
        show: false,
        name: "",
        email: "",
      },
    };
  },
  methods: {
    submitSecondForm() {
      console.log({
        name: this.secondModal.name,
        email: this.secondModal.email,
      });

      this.secondModal.name = "";
      this.secondModal.email = "";
      this.secondModal.show = false;
    },
  },
};
</script>

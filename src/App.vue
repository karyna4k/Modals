<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <!-- first modal -->
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">
            Show first modal
          </button>

          <modal
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
          </modal>

          <!-- second modal -->
          <button
            class="btn btnPrimary"
            @click="secondModal.show = !secondModal.show"
          >
            Show modal with form
          </button>

          <modal
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
          </modal>

          <!-- modal with validation -->
          <button
            class="btn btnPrimary"
            @click="modalValidate = !modalValidate"
          >
            Show modal with form + validate
          </button>

          <modalValidate v-show="modalValidate" @click="modalValidate = false">
          </modalValidate>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import modal from "@/components/UI/Modal.vue";
import modalValidate from "@/components/ModalValidate.vue";

export default {
  components: { modal, modalValidate },
  data() {
    return {
      modalFirst: false,
      secondModal: {
        show: false,
        name: "",
        email: "",
      },
      modalValidate: false,
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

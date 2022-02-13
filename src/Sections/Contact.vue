<template>
    <div class="section" id="Contact" @click="clicked">
        <div class="inside">
            <div class="contactForm mt-5">
                <h2>
                    TALK TO ME!
                </h2>
                <form id="contactForm" @submit.prevent="handleSubmit">

                    <!-- Name input -->
                    <input class="form-control" id="name" name="name" type="text" placeholder="Name" v-model="name" />

                    <!-- Email address input -->
                    <input class="form-control" id="emailAddress" name="email" type="email" placeholder="Email Address" v-model="email"/>

                    <!-- number input -->
                    <input class="form-control" id="contactNo" name="contactNo" type="text" placeholder="Phone Number" v-model="contactNo"/>

                    <!-- Message input -->
                    <textarea class="form-control" id="message" name="message" type="text" placeholder="Message" v-model="message" style="height: 10rem;"></textarea>

                    <!-- Form submit button -->
                    <div class="submit">
                        <button class="btn">SAY HI!</button>
                    </div>
                
                </form>
            </div>

        </div>
      
  </div>
</template>

<script>
export default {
    data() {
        return {
            name: '',
            email: '',
            contactNo: '',
            message: '',
        }
    },
    methods: {
        clicked() {
            this.$emit('clicked')
        },
        handleSubmit(){
            fetch('https://portfolio-backend-mugammad.herokuapp.com/contact', {
              method: 'POST', // or 'PUT'
              headers: {
                'Content-Type': 'application/json', 'Access-Control-Allow-Origin' : '*'
              },
              body: JSON.stringify({
                  name: this.name,
                  email: this.email,
                  contactNo: this.contactNo,
                  message: this.message
              }),
            })
            .then(response => response.json())
            .then(data => {
              console.log('Success:', data);
            })
            .catch((error) => {
              console.error('Error:', error);
            });
        }
    },
}
</script>
    
<style>
    #Contact {
        z-index: 5;
        background: var(--black);
    }

    .form-control {
        background-color: var(--darkgreen);
        border: 0px;
        border-radius: 0%;
        color: var(--grey);
        min-width: 100%;
        padding: 10px;
        box-sizing: border-box;
        margin: 20px 0;
    }

    .form-control:focus {
        outline: none;
        background: var(--darkgreen);
    }


</style>
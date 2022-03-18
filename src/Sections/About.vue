<template>
  <div ref="about" class="section" id="About" @click="clicked">
        <div class="inside">
            <h1>ABOUT</h1>
            <div class="line">
                
            </div>
            <div class="aboutInfo">
                <div class="myInfo">
                    <h5>Full Name: </h5><p>Mugammad Breda</p>
                </div>
                <div class="myInfo">
                    <h5>Date of Birth:</h5><p>02/05/1999</p>
                </div>
                <div class="myInfo">
                    <h5>Location:</h5><p>Cape Town, South Africa</p>
                </div>
                <div class="myInfo">
                    <h5>Cell Phone Number:</h5><p>(+27) 72 813 0202</p>
                </div>
                <div class="myInfo">
                    <h5>Email Address:</h5><p><a href="mailto:mugammadbreda1999@gmail.com">mugammadbreda1999@gmail.com</a></p>
                </div>
            </div>

            <div class="bio">
                <h3>A little About Myself</h3>
                <p>I am a quiet and confident person who engages on topics that I am passionate about. I am a hard worker and am able to
                focus and prioritise necessary tasks.</p>
                <br>
                <h3>Why I love Coding</h3>
                <p>Learning languages is one of my biggest interests right now, so I think that is where my love for coding came about. It
                is just so cool to be able to understand something you once thought you would never be able to understand. I have been
                really fascinated with art since a very young age, so I think that is why I chose web development.</p>

                <a class="btn" href="https://github.com/Mugammad/pdf/blob/main/Resume_of_MugammadBreda.pdf" download target="_blank">DOWNLOAD RESUME</a>
                <br>
                <div class="">
                    <!-- <img class="col-md-5 mt-5" src="./assets/images/signature.png" alt="" style=" opacity: 0.6;"> -->
                </div>
                
            </div>

            



        </div>
    </div>
</template>

<script>
export default {
  methods: {
    clicked() {
      this.$emit('clicked')
    }
  },
}
</script>

<style>
  .line {
  margin-top: 1rem;
  border-bottom: 6px solid var(--darkgreen);
  background: var(--darkgreen);
  width: 70px;
}

#About {
  z-index: 1;
  background: var(--black);
}

.aboutInfo {
  margin-top: 70px;
}

.myInfo {
  border-bottom: rgba(241, 250, 238, 0.5) 1px solid;
  padding: 1rem 0;
  display: flex;
  gap: 0.5rem;
}

.bio {
  margin-top: 70px;
}

.bio h3 {
  margin: 1rem 0;
}

.bio p {
  margin-bottom: 1rem;
}

.myInfo a {
  display: unset;
}

.btn {
  border-radius: 0;
  border: 3px solid var(--darkgreen);
  margin-top: 10px;
  padding: 12px 10px;
  background: var(--black);
  color: var(--grey);
  font-weight: bold;
  width: fit-content;
  transition: 0.3s;
}

.btn:hover {
  background-color: var(--darkgreen);
  border-color: var(--darkgreen);
  color: white;
  transition: 0.3s;
}
</style>
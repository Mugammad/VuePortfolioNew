<template>
  <div class="section" id="Experience" @click="clicked">
      <div class="inside">
            <h1>EXPERIENCE</h1>
            <div class="line">
            
            </div>

            <div class="header">
                <h4>
                    IT AIN'T MUCH BUT IT'S HONEST WORK
                </h4>
                <p>
                    These are just a few events that I am confident in sharing and hopefully helps me land a job.
                </p>
            </div>
            <div ref="experience" v-for="exp in experiences" :key="exp.id" class="exp grid">
                <div class="grid-1">
                    <div class="iconBox">
                        <div class="iconExp" ><i :class="exp.svg"></i></div>
                        <div class="iconLabel">
                            <h6>{{exp.name}}</h6>
                            <h4 v-for="stat in exp.status" :key="stat">{{stat}}</h4>
                            <p>{{exp.period}}</p>
                        </div>
                    </div>
                </div>
                <div class="grid-2">
                    <p>{{exp.description}}</p>
                </div>
            </div>
        </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      experiences: [
        {id: 1, svg: "fas fa-mug-hot",  name: "COFFEE SHOP", status: ["CASHIER"], period: "2015-2019", description: "I worked most weekends at a small coffee shop in Town Center, Mitchells Plain. My duties were to take orders as well as assist in the kitchen when I was needed."},
        {id: 2, svg: "fas fa-user-graduate",  name: "DARUL ARQAM", status: ["HIGH SCHOOL"], period: "2013-2017", description: "Graduated high school with a Bachelors pass. During this time I also worked part time at a small coffee shop located in Mitchells Plain."},
        {id: 3, svg: "fas fa-university",  name: "UWC", status: ["UNDERGRAD", "(INCOMPLETE)"], period: "2018-2021", description: "Studied for a Bachelors degree in Computer Science. learned Python as well as Java during this time. This is where my coding journey began and where I grew an interest in computer programming."},
        {id: 4, svg: "fas fa-laptop-code",  name: "LC ACADEMY", status: ["WEB DEV"], period: "2021-PRESENT", description: "Started learning web deveopment at a six month coding bootcamp."},
      ]
    }
  },
  methods: {
    clicked() {
      this.$emit('clicked')
    }
  },
}
</script>

<style>
  #Experience {
  z-index: 2;
  background: var(--black2);
}

.grid {
  display: grid;
  align-items: center;
  min-height: 100px;
  grid-template-columns: repeat(7, 1fr);
  grid-template-rows: 100%;
  border-bottom: 0.1px solid var(--grey);
  padding: 20px 0;
}

.gridGlobal {
  display: grid;
  align-items: center;
  grid-template-columns: repeat(7, 1fr);
  grid-template-rows: 100%;
  border-bottom: 0.1px solid var(--grey);
  padding: 20px 0;
}

.grid-1 {
  grid-column: 1/ span 3;
}

.grid-2 {
  grid-column: 4/ span 4;
}

.grid-icon-start {
  grid-column: 1/ span 1;
}

.grid-icon-end {
  grid-column: 2/ span 5;
}



.iconExp {
  font-size: 3rem;
  transition: 0.3s;
}

.iconExp:hover {
  font-size: 4rem;
  transition: 0.3s;
}

.iconLabel {
  display: block;
}

.iconBox {
  display: flex;
  align-items: center;
  gap: 10px;
}
</style>
<template>
  <div ref="home" class="section d-flex align-items-center" id="Home">
    <div class="landing">
      <div class="name col-md-4 mx-5 pt-5">
        <h1 class=" mb-0" id="hi">HI, I'M </h1>
        <h1 class="font-weight-bold display-5">MUGAMMAD</h1>
        <div class="mydscrp mt-3 d-flex justify-content-around col-md-11">
            <p>ASPIRING FULL STACK DEVELOPER</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style>

  .landing {
    background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url(../assets/images/landing/ME.jpeg);
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    background-size: cover;
    background-position: center;
    padding: 10%;
    display: flex;
    align-items: flex-end;
  }


  .mydscrp {
  border-top: 1px solid rgba(241, 250, 238, 0.5);
  border-bottom: 1px solid rgba(241, 250, 238, 0.5);
  padding: 10px 0;
  margin-top: 10px;
  display: flex;
  justify-content: space-evenly;
  width: fit-content;
}

.mydscrp > p {
  margin-bottom: 0;
}

#hi {
  font-weight: lighter;
}
</style>
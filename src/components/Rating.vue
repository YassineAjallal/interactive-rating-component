<template>
  <div class="body">
    <div class="rating" :class="{ display: display }">
      <div class="header">
        <div class="icon">
          <i class="fa-solid fa-star"></i>
        </div>
      </div>
      <div class="title">
        <h2>How Did we Do ?</h2>
      </div>
      <div class="desc">
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic omnis
          repudiandae vitae, alias quaerat dolore eveniet molestias magni.
        </p>
      </div>
      <div class="feed">
        <div
          v-for="rate in rates"
          :key="rate.key"
          :class="rate.isActive"
          @click="aciveRt(rate.key)"
        >
          {{ rate.key }}
        </div>
      </div>
      <div class="submit">
        <button @click="submitRt">Submit</button>
      </div>
    </div>
    <div class="afterRt" :class="{ dontDisplay: dontDisplay }">
      <div class="icon">
        <i class="fa-sharp fa-solid fa-blender-phone"></i>
      </div>
      <div class="nbrt">You selected {{ numberRt }} out of 5</div>
      <div class="title">
        <h2>Thank You !</h2>
      </div>
      <div class="desc">
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic omnis
          repudiandae vitae, alias quaerat dolore eveniet molestias magni.
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      rates: [
        { key: 1, isActive: "" },
        { key: 2, isActive: "" },
        { key: 3, isActive: "" },
        { key: 4, isActive: "" },
        { key: 5, isActive: "" },
      ],
      numberRt: 0,
      display: true,
      dontDisplay: false,
    };
  },
  methods: {
    aciveRt(rate) {
      this.rates.map((t) => {
        if (t.key === rate) t.isActive = "active";
        else t.isActive = "";
        return 0;
      });
    },
    submitRt() {
      this.rates.map((t) => {
        if (t.isActive === "active") this.numberRt = t.key;
        return 0;
      });
      this.display = !this.display;
      this.dontDisplay = !this.dontDisplay;
    },
  },
};
</script>
<style>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
.body,
.icon,
.feed div,
.submit,
.nbrt {
  display: flex;
  justify-content: center;
  align-items: center;
}
.body,
.header,
.title,
.desc,
.feed,
.submit,
.submit button {
  width: 100%;
}
.body {
  font-weight: 400;
  height: 100vh;
  background-color: hsl(216, 12%, 8%);
}
.rating,
.afterRt {
  padding: 15px;
  width: 26%;
  height: 30vh;
  display: flex;
  border-radius: 25px;
  justify-content: space-around;
  flex-direction: column;
  align-items: center;
  background-color: hsl(213, 19%, 18%);
  transition: 0.3s;
  opacity: 0;
  transform: translateX(50%);
}
.afterRt .header,
.afterRt .title,
.after .desc {
  text-align: center;
}

.header,
.title,
.desc {
  text-align: left;
}
.icon,
.feed div {
  width: 55px;
  height: 55px;
  background-color: hsl(216, 12%, 8%);
  border-radius: 50%;
}
.icon i {
  color: hsl(25, 97%, 53%);
  font-size: 20px;
}
.desc p {
  font-size: 15px;
  color: #ddd;
  line-height: 1.7;
}
.title h2 {
  color: hsl(0, 0%, 100%);
  font-weight: bold;
}
.feed {
  display: flex;
  justify-content: space-around;
}
.feed div {
  color: hsl(0, 0%, 100%);
  transition: 0.3s;
  cursor: pointer;
}
.feed div:hover {
  background-color: hsl(216, 12%, 54%);
}
.active {
  background-color: hsl(25, 97%, 53%) !important;
}
.submit {
  height: 50px;
}
.submit button {
  height: 100%;
  border-radius: 35px;
  color: hsl(25, 97%, 53%);
  background-color: hsl(0, 0%, 100%);
  outline: none;
  border: none;
  font-size: 16px;
  text-transform: uppercase;
  letter-spacing: 2px;
  cursor: pointer;
}
.nbrt {
  width: 60%;
  height: 30px;
  border-radius: 15px;
  font-weight: bold;
  color: hsl(25, 97%, 53%);
  background-color: hsl(216, 12%, 8%);
}
.display {
  opacity: 1;
}
.dontDisplay {
  opacity: 1;
  transform: translateX(-50%);
}
</style>
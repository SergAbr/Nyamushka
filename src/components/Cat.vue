<template>
  <div class="cat">
    <div
      :class="{ cat__clicked: this.clicked, cat__disabled: cat.disabled }"
      class="cat__border"
    >
      <div
        :class="{
          cat__ishover: this.isHover,
        }"
        class="cat__wrapper"
        @click="catClick"
        @mouseover="catHover"
        @mouseout="catMouseOut"
      >
        <div class="cat__feed">{{ cat.title }}</div>
        <div class="cat__name">{{ cat.name }}</div>
        <div class="cat__taste">{{ cat.taste }}</div>
        <div class="cat__purchase-info">
          <p>
            <span class="cat__portion">
              {{ cat.portionCount }}
            </span>
            {{ cat.portion }}
          </p>
          <p>
            <span class="cat__mouses">
              {{ cat.mousesCount }}
            </span>
            {{ cat.mouses }}
          </p>
        </div>
        <div
          :class="{
            cat__weight__clicked: this.clicked,
            cat_weight__disabled: cat.disabled,
          }"
          class="cat__weight-label"
        >
          <div class="cat__amount">{{ cat.amount }}</div>
          <div class="cat__unit">{{ cat.unit }}</div>
        </div>
      </div>
    </div>
    <div>
      <div class="cat__descript" v-if="this.clicked">{{ cat.selected }}</div>
      <div
        class="cat__descript distext"
        v-else-if="this.disabled !== cat.disabled"
      >
        {{ cat.distext }}
      </div>
      <div class="cat__descript" v-else>
        Чего сидишь? Порадуй котэ, <a @click="catClick">купи.</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      disabled: false,
      clicked: false,
      isHover: false,
      isMouseOut: false,
    };
  },
  props: {
    cat: {
      type: Object,
      required: true,
    },
  },
  methods: {
    catClick() {
      this.clicked = !this.clicked;
      this.isHover = false;
    },
    catHover() {
      if (!this.cat.disabled) {
        this.isHover = true;
      }
    },
    catMouseOut() {
      if ((this.isHover = true)) {
        this.isHover = false;
      }
    },
  },
};
</script>

<style scoped>
.cat {
  margin-bottom: 20px;
}
.cat__wrapper {
  background: linear-gradient(
    135deg,
    transparent 28px,
    transparent 0,
    #f2f2f2 0
  );
  width: 320px;
  height: 480px;
  border: 4px solid transparent;
  background-clip: padding-box;
  border-radius: 15px;
  padding: 17px 12px 12px 47px;
  position: relative;
  overflow: hidden;
  cursor: pointer;
}

.cat__wrapper:before {
  content: '';
  position: absolute;
  height: 88px;
  width: 88px;
  background: transparent;
  transform: rotate(45deg);
  top: -48px;
  left: -67px;
}
.cat__wrapper:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  background: left 0px top -8px/308px 480px no-repeat url(@/assets/cat.png);
  height: 480px;
  width: 320px;
  pointer-events: none;
}

.cat__border {
  background: linear-gradient(
    135deg,
    transparent 30px,
    transparent 0,
    #1698d9 0
  );
  border-radius: 12px;
}

.cat__image {
  position: absolute;
  top: 0;
  left: 0;
}
.cat__feed {
  font-size: 16px;
  color: #666666;
}
.cat__name {
  font-size: 48px;
  font-weight: 800;
}
.cat__taste {
  font-size: 24px;
  font-weight: 700;
}
.cat__purchase-info {
  width: 180px;
  color: #666666;
  font-size: 14px;
  margin-top: 15px;
}
.cat__portion,
.cat__mouses {
  font-weight: 700;
}
.cat__weight-label {
  position: absolute;
  right: 12px;
  bottom: 12px;
  background: #1698d9;
  color: #fff;
  border-radius: 50%;
  height: 80px;
  width: 80px;
  padding: 15px 0 12px;
  text-align: center;
  box-sizing: border-box;
  z-index: 1;
  pointer-events: none;
}
.cat__amount {
  font-size: 42px;
  line-height: 32px;
}
.cat__unit {
  font-size: 21px;
  line-height: 27px;
}
.cat__descript {
  color: #ffffff;
  font-size: 13px;
  line-height: 15px;
  text-align: center;
  margin-top: 15px;
}

.cat__descript a {
  text-decoration: none;
  color: #2ea8e6;
  cursor: pointer;
  border-bottom: 1px dashed #2ea8e6;
}

.cat__disabled {
  opacity: 0.8;
  pointer-events: none;
  background: linear-gradient(
    135deg,
    transparent 30px,
    transparent 0,
    #b3b3b3 0
  );
  background-clip: padding-box;
}
.cat_weight__disabled {
  background: #b3b3b3;
}
.distext {
  color: yellow;
}
.cat__clicked {
  transition: all 0.1s;
  background: linear-gradient(
    135deg,
    transparent 30px,
    transparent 0,
    #d91667 0
  );
}
.cat__weight__clicked {
  transition: all 0.1s;
  background: #d91667;
}
.cat__ishover {
  background: linear-gradient(
    135deg,
    transparent 28px,
    transparent 0,
    #fff7fb 0
  );
  background-clip: padding-box;
}
</style>

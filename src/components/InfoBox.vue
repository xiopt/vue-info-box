<template lang="html">
  <div :class="classType" v-if="isActive">
    <h3 v-html="titleType"></h3>
    <p>
      <slot name="box-body"></slot>
    </p>
  </div>
</template>

<script>
export default {
  name: "Box",
  data() {
    return {
      isActive: false,
      boxType: 'info'
    }
  },
  props: {
    active: {
      type: Boolean,
      required: true,
      default: false
    },
    type: {
      type: String,
      required: true,
      default: 'info'
    }
  },
  created() {
    this.isActive = this.active
    this.boxType = this.type
  },
  methods: {

  },
  computed: {
    titleType: function() {
      switch (this.boxType) {
        case 'info':
          return '<i class="fa fa-info-circle"></i> Info';

        case 'warning':
          return '<i class="fa fa-exclamation-circle"></i> Warning';

        case 'error':
          return '<i class="fa fa-times-circle"></i> Error';

        case 'confirm':
          return '<i class="fa fa-check-circle"></i> Success';

        default:
          return '<i class="fa fa-info-circle"></i> Info';

      }
    },
    classType: function() {
      switch (this.boxType) {
        case 'info':
          return {
            'tut-info-box': true
          }

        case 'warning':
          return {
            'tut-info-box warning': true
          }

        case 'error':
          return {
            'tut-info-box error': true
          }

        case 'confirm':
          return {
            'tut-info-box confirm': true
          }

        default:
          return {
            'tut-info-box confirm': true
          }
      }
    }
  }
}
</script>

<style lang="css">
.tut-info-box {
background: rgba(239, 239, 239, 0.17);
border: 2px solid #01c1ec;
padding: 5px;
-webkit-font-smoothing: antialiased;
font-family: Helvetica;
margin: 25px 0px;
margin-top: 5px !important;
}

.tut-info-box h3 {
  font-family: Helvetica;
  font-weight: bold;
  color: white;
  background: #01c1ec;
  margin: -5px -5px 0px -5px;
  padding: 5px;
  vertical-align: middle;
  font-size: 13px;
}

.tut-info-box.confirm {
border: 2px solid rgb(124, 223, 124);
}

.tut-info-box.confirm h3 {
background: rgb(124, 223, 124);
}

.tut-info-box.error{
border:2px solid rgb(223, 114, 114);
}

.tut-info-box.error h3 {
background: rgb(223, 114, 114);
}

.tut-info-box.warning {
border: 2px solid rgb(255, 165, 36);
}

.tut-info-box.warning h3{
border: 2px solid rgb(255, 165, 36);
background: rgb(255, 165, 36);
}

.tut-info-box p {
font-family: Helvetica;
font-size: 11px;
padding: 10px 5px;
}
</style>

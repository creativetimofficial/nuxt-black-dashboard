<template>
  <div class="row">
    <div class="col-md-6">
      <card>
        <h4 slot="header" class="card-title">Notifications Style</h4>

        <base-alert type="info"> This is a plain notification</base-alert>

        <base-alert type="info" dismissible>
          This is a notification with close button.
        </base-alert>

        <base-alert type="info" dismissible icon="tim-icons icon-bell-55">
          This is a notification with close button and icon.
        </base-alert>

        <base-alert type="info" dismissible icon="tim-icons icon-bell-55">
          This is a notification with close button and icon and have many lines.
          You can see that the icon and the close button are always vertically
          aligned. This is a beautiful notification. So you don't have to worry
          about the style.
        </base-alert>
      </card>
    </div>

    <div class="col-md-6">
      <card>
        <h4 slot="header" class="card-title">Notification states</h4>

        <base-alert type="primary" dismissible>
          <span
            ><b> Primary - </b> This is a regular notification made with
            ".alert-primary"</span
          >
        </base-alert>

        <base-alert type="info" dismissible>
          <span
            ><b> Info - </b> This is a regular notification made with
            ".alert-info"</span
          >
        </base-alert>

        <base-alert type="success" dismissible>
          <span
            ><b> Success - </b> This is a regular notification made with
            ".alert-success"</span
          >
        </base-alert>

        <base-alert type="warning" dismissible>
          <span
            ><b> Warning - </b> This is a regular notification made with
            ".alert-warning"</span
          >
        </base-alert>

        <base-alert type="danger" dismissible>
          <span
            ><b> Danger - </b> This is a regular notification made with
            ".alert-danger"</span
          >
        </base-alert>
      </card>
    </div>
    <div class="col-md-12">
      <card class="text-center">
        <div class="places-buttons">
          <div class="row">
            <div class="col-md-6 ml-auto mr-auto text-center">
              <h4 class="card-title">
                Notifications Places
                <p class="category">Click to view notifications</p>
              </h4>
            </div>
          </div>
          <div class="row">
            <div class="col-lg-8 ml-auto mr-auto">
              <div class="row">
                <div class="col-md-4">
                  <base-button
                    type="primary"
                    block
                    @click.native="notifyVue('top', 'left')"
                    >Top Left
                  </base-button>
                </div>
                <div class="col-md-4">
                  <base-button
                    type="primary"
                    block
                    @click.native="notifyVue('top', 'center')"
                    >Top Center
                  </base-button>
                </div>
                <div class="col-md-4">
                  <base-button
                    type="primary"
                    block
                    @click.native="notifyVue('top', 'right')"
                    >Top Right
                  </base-button>
                </div>
              </div>
            </div>
          </div>
          <div class="row">
            <div class="col-lg-8 ml-auto mr-auto">
              <div class="row">
                <div class="col-md-4">
                  <base-button
                    type="primary"
                    block
                    @click.native="notifyVue('bottom', 'left')"
                    >Bottom Left
                  </base-button>
                </div>
                <div class="col-md-4">
                  <base-button
                    type="primary"
                    block
                    @click.native="notifyVue('bottom', 'center')"
                    >Bottom Center
                  </base-button>
                </div>
                <div class="col-md-4">
                  <base-button
                    type="primary"
                    block
                    @click.native="notifyVue('bottom', 'right')"
                    >Bottom Right
                  </base-button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </card>
    </div>
  </div>
</template>
<script>
import { BaseAlert } from '@/components';

export default {
  name: 'notifications',
  components: {
    BaseAlert
  },
  data() {
    return {
      type: ['', 'info', 'success', 'warning', 'danger'],
      notifications: {
        topCenter: false
      },
    };
  },
  methods: {
    notifyVue(verticalAlign, horizontalAlign) {
      let color = Math.floor(Math.random() * 4 + 1);
      this.$notify({
        message:
          'Welcome to <b>Vue Black Dashboard Pro</b> - a beautiful resource for every web developer',
        timeout: 30000,
        icon: 'tim-icons icon-bell-55',
        horizontalAlign: horizontalAlign,
        verticalAlign: verticalAlign,
        type: this.type[color]
      });
    }
  }
};
</script>
<style>
.card .alert {
  position: relative !important;
  width: 100%;
}
</style>

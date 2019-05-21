<template>
  <q-layout>
    <q-page-container>
      <q-page class="q-ma-md">
        <q-dialog
          v-model="dialog"
          persistent
          :maximized="true"
          transition-show="slide-up"
          transition-hide="slide-down"
        >
          <q-layout class="bg-white">
            <q-toolbar class="bg-primary text-white">
              <q-toolbar-title>Collection Payment</q-toolbar-title>

              <q-btn flat round dense icon="fas fa-times" size="10px" @click="dialog = false"/>
            </q-toolbar>
            <q-card flat>
              <q-card-section>
                <q-item class="q-pa-none">
                  <q-item-section>
                    <q-item-label class="text-subtitle2">ABC - CENTER 101
                      <q-badge color="info">ALBAY</q-badge>
                    </q-item-label>
                    <q-item-label class="text-subtitle2">05/21/2019</q-item-label>
                    <q-item-label class="text-h6">
                      0.00
                      <span class="text-grey">●</span> 10,000.00
                    </q-item-label>
                  </q-item-section>
                  <q-item-section side>
                    <q-badge color="positive">
                      <span class="text-subtitle2">{{ 5000 | currency('') }}</span>
                    </q-badge>
                  </q-item-section>
                </q-item>
                <q-separator class="q-mt-sm"/>
                <q-tab-panels v-model="tab" animated>
                  <q-tab-panel class="q-pa-none" name="clients">
                    <div class="text-h6">Clients</div>
                    <q-select dense v-model="model" :options="options" label="Search"/>
                    <q-list class="q-pa-none">
                      <q-item class="q-px-xs">
                        <q-item-section>
                          <q-item-label class="text-weight-bold">
                            <q-avatar size="26px" color="primary">
                              <span class="text-white">1</span>
                            </q-avatar>Maria Juan Dela Cruz
                          </q-item-label>
                          <q-item-label>
                            <q-icon name="fas fa-money-bill-alt" color="orange" size="24px"></q-icon>1,200.00
                          </q-item-label>
                          <div class="row">
                            <div class="col">
                              <q-icon name="fas fa-first-aid" color="red" size="18px"></q-icon>
                            </div>
                          </div>
                        </q-item-section>

                        <q-item-section side top>
                          <div>
                            <q-popup-edit v-model="payment1" buttons>
                              <q-input type="number" v-model="payment1" dense autofocus/>
                            </q-popup-edit>
                            <q-item-label class="text-h6">{{ payment1 }}</q-item-label>
                          </div>

                          <q-item-label class="text-h6">
                            <q-badge color="blue">
                              <select name="select">
                                <option value="P" selected>PRESENT</option>
                                <option value="U">UNDERTIME</option>
                                <option value="T">TARDY</option>
                                <option value="A">ABSENT</option>
                                <option value="L">LEAVE</option>
                                <option value="I">INACTIVE</option>
                                <option value="E">EXCUSED</option>
                              </select>
                            </q-badge>
                          </q-item-label>
                        </q-item-section>
                      </q-item>

                      <q-separator inset></q-separator>

                      <q-item class="q-px-xs">
                        <q-item-section>
                          <q-item-label class="text-weight-bold">
                            <q-avatar size="24px" color="primary">
                              <span class="text-white">2</span>
                            </q-avatar>Juana Consolacion
                          </q-item-label>
                          <q-item-label>
                            <q-icon name="money" color="orange" size="24px"></q-icon>1,200.00
                          </q-item-label>
                          <div class="row">
                            <div class="col">
                              <q-icon name="star" color="yellow" size="20px"></q-icon>
                              <q-icon name="star" color="yellow" size="20px"></q-icon>
                              <q-icon name="star" color="yellow" size="20px"></q-icon>
                            </div>
                          </div>
                        </q-item-section>

                        <q-item-section side top>
                          <div>
                            <q-popup-edit v-model="payment2" buttons>
                              <q-input type="number" v-model="payment2" dense autofocus/>
                            </q-popup-edit>
                            <q-item-label class="text-h6">{{ payment2 }}</q-item-label>
                          </div>

                          <q-item-label class="text-h6">
                            <q-badge color="red">
                              <select name="select">
                                <option value="P">PRESENT</option>
                                <option value="U">UNDERTIME</option>
                                <option value="T">TARDY</option>
                                <option value="A" selected>ABSENT</option>
                                <option value="L">LEAVE</option>
                                <option value="I">INACTIVE</option>
                                <option value="E">EXCUSED</option>
                              </select>
                            </q-badge>
                          </q-item-label>
                        </q-item-section>
                      </q-item>
                    </q-list>
                    <span class="q-ma-lg"></span>
                  </q-tab-panel>
                  <q-tab-panel class="q-pa-none" name="center_savings">
                    <div class="text-h6">Center Savings</div>Lorem ipsum dolor sit amet consectetur adipisicing elit.
                  </q-tab-panel>
                  <q-tab-panel class="q-pa-none" name="center_release">
                    <div class="text-h6">Center Releases</div>Lorem ipsum dolor sit amet consectetur adipisicing elit.
                  </q-tab-panel>
                </q-tab-panels>
                <!-- <q-item-section avatar>
                      
                      <q-item-label>Maria Juana Dela Cruz</q-item-label>
                      <q-item-label caption lines="1">client@sedp.ph</q-item-label>
                    </q-item-section>
                    <q-item-section>
                      <q-item-label>Maria Juana Dela Cruz</q-item-label>
                      <q-item-label caption lines="1">client@sedp.ph</q-item-label>
                </q-item-section>-->
              </q-card-section>
            </q-card>
            <q-page-sticky expand position="bottom">
              <div class="row full-width">
                <div class="col">
                  <q-tabs v-model="tab" dense switch-indicator class="bg-grey-2 text-primary">
                    <q-tab class="text-green" name="clients" icon="fas fa-users"/>

                    <q-tab class="text-orange" name="center_savings" icon="fas fa-piggy-bank"/>

                    <q-tab class="text-blue" name="center_release" icon="fas fa-wallet"/>
                  </q-tabs>
                </div>
              </div>
            </q-page-sticky>
          </q-layout>
        </q-dialog>
        <div class="q-pa-md" style="max-width: 360px">
          <q-list>
            <q-item>
              <q-item-section>
                <q-item-label class="text-weight-bold">
                  <q-avatar size="26px" color="primary">
                    <span class="text-white">1</span>
                  </q-avatar>Maria Juan Dela Cruz
                </q-item-label>
                <q-item-label>
                  <q-icon name="fas fa-money-bill-alt" color="orange" size="24px"></q-icon>1,200.00
                </q-item-label>
                <div class="row">
                  <div class="col">
                    <q-icon name="fas fa-first-aid" color="red" size="18px"></q-icon>
                  </div>
                </div>
              </q-item-section>

              <q-item-section side top>
                <div>
                  <q-popup-edit v-model="payment1" buttons>
                    <q-input type="number" v-model="payment1" dense autofocus/>
                  </q-popup-edit>
                  <q-item-label class="text-h6">{{ payment1 }}</q-item-label>
                </div>

                <q-item-label class="text-h6">
                  <q-badge color="blue">
                    <select name="select">
                      <option value="P" selected>PRESENT</option>
                      <option value="U">UNDERTIME</option>
                      <option value="T">TARDY</option>
                      <option value="A">ABSENT</option>
                      <option value="L">LEAVE</option>
                      <option value="I">INACTIVE</option>
                      <option value="E">EXCUSED</option>
                    </select>
                  </q-badge>
                </q-item-label>
              </q-item-section>
            </q-item>

            <q-separator inset></q-separator>

            <q-item>
              <q-item-section>
                <q-item-label class="text-weight-bold">
                  <q-avatar size="24px" color="primary">
                    <span class="text-white">2</span>
                  </q-avatar>Juana Consolacion
                </q-item-label>
                <q-item-label>
                  <q-icon name="money" color="orange" size="24px"></q-icon>1,200.00
                </q-item-label>
                <div class="row">
                  <div class="col">
                    <q-icon name="star" color="yellow" size="20px"></q-icon>
                    <q-icon name="star" color="yellow" size="20px"></q-icon>
                    <q-icon name="star" color="yellow" size="20px"></q-icon>
                  </div>
                </div>
              </q-item-section>

              <q-item-section side top>
                <div>
                  <q-popup-edit v-model="payment2" buttons>
                    <q-input type="number" v-model="payment2" dense autofocus/>
                  </q-popup-edit>
                  <q-item-label class="text-h6">{{ payment2 }}</q-item-label>
                </div>

                <q-item-label class="text-h6">
                  <q-badge color="red">
                    <select name="select">
                      <option value="P">PRESENT</option>
                      <option value="U">UNDERTIME</option>
                      <option value="T">TARDY</option>
                      <option value="A" selected>ABSENT</option>
                      <option value="L">LEAVE</option>
                      <option value="I">INACTIVE</option>
                      <option value="E">EXCUSED</option>
                    </select>
                  </q-badge>
                </q-item-label>
              </q-item-section>
            </q-item>

            <q-separator inset></q-separator>

            <q-item>
              <q-item-section>
                <q-item-label>Single line item</q-item-label>
                <q-item-label
                  caption
                >Secondary line text. Lorem ipsum dolor sit amet, consectetur adipiscit elit.</q-item-label>
              </q-item-section>

              <q-item-section side top>
                <q-item-label caption>Voted!</q-item-label>
              </q-item-section>
            </q-item>

            <q-separator spaced inset></q-separator>

            <q-item>
              <q-item-section>
                <q-item-label>Single line item</q-item-label>
                <q-item-label
                  caption
                >Secondary line text. Lorem ipsum dolor sit amet, consectetur adipiscit elit.</q-item-label>
              </q-item-section>

              <q-item-section side top>
                <q-badge color="teal" label="10k"></q-badge>
              </q-item-section>
            </q-item>

            <q-separator spaced inset></q-separator>

            <q-item>
              <q-item-section>
                <q-item-label>Single line item</q-item-label>
                <q-item-label
                  caption
                >Secondary line text. Lorem ipsum dolor sit amet, consectetur adipiscit elit.</q-item-label>
              </q-item-section>

              <q-item-section side top>
                <q-item-label caption>2 min ago</q-item-label>
                <div class="text-orange">
                  <q-icon name="star"></q-icon>
                  <q-icon name="star"></q-icon>
                  <q-icon name="star"></q-icon>
                </div>
              </q-item-section>
            </q-item>

            <q-separator spaced inset></q-separator>

            <q-item>
              <q-item-section>
                <q-item-label>Single line item</q-item-label>
                <q-item-label
                  caption
                >Secondary line text. Lorem ipsum dolor sit amet, consectetur adipiscit elit.</q-item-label>
              </q-item-section>

              <q-item-section side top>
                <q-item-label caption>meta</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </div>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      tab: "clients",
      dialog: true,
      payment1: 200.51,
      payment2: 0
    };
  }
};
</script>

<style>
select {
  background-color: transparent;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  border: none;
  /* needed for Firefox: */
  overflow: hidden;
  width: 120%;
  text-align-last: center;
  color: white;
}

select option {
  color: black;
}
</style>

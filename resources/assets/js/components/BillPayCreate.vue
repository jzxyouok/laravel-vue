<template>
    <div class="container">
        <div class="row">
            <div class="col m8 offset-m2">
                <h4 class="center-align">Nova Conta a pagar</h4>
                <div class="row">
                    <form class="col s12">
                        <div class="row">
                          <div class="input-field col s12">
                              <input placeholder="Nome da conta a pagar" type="text" id="name" v-model="bill.name">
                              <label for="name">Nome</label>
                          </div>
                        </div>
                        <div class="row">
                          <div class="input-field col s12">
                              <input placeholder="Data De vencimento" type="text" id="date_due" v-model="bill.date_due">
                              <label for="date_due">Data de Vencimento</label>
                          </div>
                        </div>
                        <div class="row">
                          <div class="input-field col s12">
                              <input placeholder="Valor" type="text" id="value" v-model="bill.value">
                              <label for="value" class="active">Valor</label>
                          </div>
                        </div>
                        <div class="row">
                            <div class="col m12">
                                <p class="center-align">
                                    <button class="btn btn-large btn-default" type="button" @click="submit()">Criar</button>
                                </p>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return {
              bill: {
                  name: '',
                  date_due: '',
                  value: 0
              }
            };
        },
        methods: {
            submit(){
                  this.$http.post(`http://localhost:8000/api/bill_pays/`, this.bill).then((response) => {
                  this.$router.go({name: 'bill-pay.list'});
                });
            }
        }
    }
</script>

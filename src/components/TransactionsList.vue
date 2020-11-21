<template>
    <div class="transactions">
        <div class="balance">            
                <span class="currentAmount">${{ this.allTransactions[0].AvailableBalance.toFixed(2) }}</span>
                <span class="balanceTitle">Starting Balance</span>        
        </div>
        <h1>Latest Transactions</h1>
            <div class="latest" v-for="(transaction, index) in allTransactions" :key="index">
                <div class="transaction"  v-if="transaction.Billed">                
                    <div class="transLeft">
                        <span class="date"><em>{{ new Date(transaction.TransactionDate).toString().slice(0,21)}}</em></span>
                        <span class="merchName">{{ transaction.MerchantName }}</span>
                        <span class="transDesc">{{ transaction.Description }}</span>
                    </div>
                    <div class="transRight">
                        <span class="transAmount"><strong>-{{ transaction.Amount.toFixed(2) }}</strong></span>
                        <span class="remainBalance"><em>({{ remainingBalance[index].toFixed(2) }})</em></span>
                    </div>   
                </div>
            </div>
        <hr />
          <div class="balanceRow">
                <div class="transLeft">
                   <span class="merchName">Current Balance</span>
                </div>
                <div class="transRight">
                    <span class="balanceAmount">${{ remainingBalance[this.allTransactions.length - 1].toFixed(2) }}</span>
                </div>   
            </div>
        <h1>Pending Transactions</h1>
        <div class="pending" v-for="(transaction, index) in allTransactions" :key="index + 100">
            <div class="transaction"  v-if="!transaction.Billed">
                <div class="transLeft">
                    <span class="date"><em>{{ new Date(transaction.TransactionDate).toString().slice(0,21)}}</em></span>
                    <span class="merchName">{{ transaction.MerchantName }}</span>
                    <span class="transDesc">{{ transaction.Description }}</span>
                </div>
                <div class="transRight">
                    <span class="transAmount"><strong>-{{ transaction.Amount.toFixed(2) }}</strong></span>
                    <span class="remainBalance"><em>({{ potentialBalance[index].toFixed(2) }})</em></span>
                </div>   
            </div>
        </div>
        <hr />
            <div class="balanceRow">
                <div class="transLeft">
                    <span class="merchName">Ending Balance</span>
                    <span class="transDesc">(After all transactions completed)</span>
                </div>
                <div class="transRight">
                    <span class="balanceAmount">${{potentialBalance[this.allTransactions.length - 1].toFixed(2)}}</span>
                </div>   
            </div>
    </div>
</template>

<script>
import {mapGetters} from 'vuex';
export default {
    name: 'TransactionsList',
    computed: {
        ...mapGetters(['allTransactions']),
            remainingBalance: function () {
                var availableBalance = this.allTransactions[0].AvailableBalance;
                return this.allTransactions.map((transaction) => {
                    if(transaction.Billed){                        
                        return availableBalance -= transaction.Amount
                    }
                });
            },
            potentialBalance: function () {
                var availableBalance = this.allTransactions[0].AvailableBalance;
                return this.allTransactions.map((transaction) => {                                           
                        return availableBalance -= transaction.Amount                    
                });
            }
        },
}
</script>

<style scoped>
    hr {
        color: black;
        width: 100%;
    }
    .transactions{
        display: grid;
        width: 75vw;
    }
    .transaction{
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        padding: 20px 0;
        border-top: 1px solid #9c9a9a;
    }
    .balanceRow{
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        margin-bottom: 20px;
    }
    .transRight{
        display: flex;
        flex-direction: column;
        align-items: flex-end;
        justify-content: center;
    }

    .transAmount{
        font-size: 1.5rem;
    }
    .transLeft{
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;
    }

    .merchName{
        font-size: 2rem;
    }
    .balance{
        display: grid;
        grid-template-rows: repeat(2, 1fr);
    }
    .balanceContainer{
        display: grid;
        grid-template-rows: repeat(2, 1fr);
    }
    .currentAmount{
        font-size: 4rem;
        color: #056839;
    }
    .balanceAmount{
        font-size: 2rem;
    }

    .balanceTitle{
        font-size: 1rem;
    }
    .latest {
        color: #f04a4a;
    }
    .pending {
        color: #fd892a;
    }
    .info{
        font-size: 0.5rem;
    }
    .date{
        font-size: .75rem;
    }
</style>
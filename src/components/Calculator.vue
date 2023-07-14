<template>
    <div>
        <div class="calculator">
            <Screen class="screen" :val="this.expression" />
            <Button @click="append('7')" :value="7"/>
            <Button @click="append('8')" :value="8"/>
            <Button @click="append('9')" :value="9"/>
            <Symbol @click="multiply" :bgColor="'grey'" :sign="'*'"/>
            <Button @click="append('4')" :value="4"/>
            <Button @click="append('5')" :value="5"/>
            <Button @click="append('6')" :value="6"/>
            <Symbol @click="divide" :bgColor="'grey'" :sign="'/'"/>
            <Button @click="append('1')" :value="1"/>
            <Button @click="append('2')" :value="2"/>
            <Button @click="append('3')" :value="3"/>
            <Symbol @click="sub" :bgColor="'grey'" :sign="'-'"/>
            <Symbol @click="clear" :bgColor="'red'" :sign="'C'"/>
            <Button @click="append('0')" :value="0"/>
            <Symbol @click="dot" :bgColor="'grey'" :sign="'.'"/>
            <Symbol @click="add" :bgColor="'grey'" :sign="'+'"/>
            <Symbol @click="changeSign" :bgColor="'grey'" :sign="'+/-'"/>
            <Symbol @click="percent" :bgColor="'grey'" :sign="'%'"/>
            <Symbol class="equal" @click="equals" :bgColor="'grey'" :sign="'='"/>
        </div>
        <h3>Built By <a href="https://purav-parekh.netlify.app" target="_blank">Purav Parekh</a></h3>
    </div>
</template>


<script>
    import Screen from './Screen.vue'
    import Button from './Button.vue' 
    import Symbol from './Symbol.vue'


export default {
  name: 'App',
  components: {
    Screen,
    Button,
    Symbol
  },
  data () {
    return {
        prev: null,
        expression: '' || '0',
        operator: null,
        operatorClicked: false
    }
  },
  methods: {
    append(num) {
        if(this.operatorClicked) {
            this.expression = ''
            this.operatorClicked = false
        }
        if(this.expression.charAt(0) === '0')
            this.expression = num
        else this.expression += num
    },
    dot() {
        if(this.expression.indexOf('.') === -1) {
            this.expression += '.'
        }
    },
    switchExpression() {
        this.prev = this.expression;
        this.operatorClicked = true;
    },
    add() {
        this.operator = (a,b) => a+b
        this.switchExpression()
    },
    sub() {
        this.operator = (a,b) => a-b
        this.switchExpression()
    },
    multiply() {
        this.operator = (a,b) => a*b
        this.switchExpression()
    },
    divide() {
        this.operator = (a,b) => a/b;
        this.switchExpression()
    },
    clear() {
        this.expression = "0"
    },
    changeSign() {
        if(this.expression.charAt(0) !== '0') {
            this.expression = this.expression.charAt(0) === '-' ? this.expression.slice(1) : `-${this.expression}`
        }
    },
    percent() {
        this.expression = `${parseFloat(this.expression)/100}`
    },
    equals() {
        this.expression = `${this.operator(parseFloat(this.prev),parseFloat(this.expression))}`
        this.operatorClicked = true
        this.prev = null
    }
  }
}
</script>

<style scoped>
    .calculator {
        display: grid;
        grid-template-columns: repeat(4 / 1fr);
        grid-auto-rows: minmax(50px,auto);
        margin: auto;
        max-width: 17em
    }

    .screen {
        grid-column: 1/5;
        display: flex;
        flex-direction: column-reverse;
        align-items: self-end;
        color: black;
        padding: 5px;
    }


    .equal {
        grid-column-start: 3;
        grid-column-end: 5;
    }

</style>
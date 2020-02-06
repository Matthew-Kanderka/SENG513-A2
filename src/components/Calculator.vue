<template>
    <div class="container">

        <div class="row">
            <div class="col-12">
                <div id="resultField">{{result}}</div>
            </div>
        </div>

        <div class="row">
            <div class="col-12">
                <div id="input">{{currentExpression}}</div>
            </div>
        </div>


        <div class="row">
            <div class="col">
                <button type="button" @click="leftBracket()" class="btn btn-primary btn-block mb-2">(</button>
            </div>
            <div class="col">
                <button type="button" @click="rightBracket()" class="btn btn-primary btn-block">)</button>
            </div>
            <div class="col">
                <button type="button" @click="getPreviousAnswer()" class="btn btn-primary btn-block">Ans</button>
            </div>
            <div class="col-4">
                <button type="button" @click="backspace()" class="btn btn-primary btn-block">CE</button>
            </div>
            <div class="col-4">
                <button type="button" @click="clear()" class="btn btn-primary btn-block">C</button>
            </div>
        </div>

        <div class="row">
            <div class="col">
                <button type="button" @click="press(7)" class="btn btn-primary btn-block">7</button>
            </div>
            <div class="col">
                <button type="button" @click="press(8)" class="btn btn-primary btn-block">8</button>
            </div>
            <div class="col">
                <button type="button" @click="press(9)" class="btn btn-primary btn-block">9</button>
            </div>
            <div class="col">
                <button type="button" @click="divide()" class="btn btn-primary btn-block">/</button>
            </div>
        </div>

        <div class="row">
            <div class="col">
                <button type="button" @click="press(4)" class="btn btn-primary btn-block">4</button>
            </div>
            <div class="col">
                <button type="button" @click="press(5)" class="btn btn-primary btn-block">5</button>
            </div>
            <div class="col">
                <button type="button" @click="press(6)" class="btn btn-primary btn-block">6</button>
            </div>
            <div class="col">
                <button type="button" @click="multiply()" class="btn btn-primary btn-block">x</button>
            </div>
        </div>

        <div class="row">
            <div class="col">
                <button type="button" @click="press(1)" class="btn btn-primary btn-block">1</button>
            </div>
            <div class="col">
                <button type="button" @click="press(2)" class="btn btn-primary btn-block">2</button>
            </div>
            <div class="col">
                <button type="button" @click="press(3)" class="btn btn-primary btn-block">3</button>
            </div>
            <div class="col">
                <button type="button" @click="minus()" class="btn btn-primary btn-block">-</button>
            </div>
        </div>

        <div class="row">
            <div class="col">
                <button type="button" @click="press(0)" class="btn btn-primary btn-block">0</button>
            </div>
            <div class="col">
                <button type="button" @click="period()" class="btn btn-primary btn-block">.</button>
            </div>
            <div class="col">
                <button type="button" @click="calculate(currentExpression)" class="btn btn-primary btn-block">=</button>
            </div>
            <div class="col">
                <button type="button" @click="plus()" class="btn btn-primary btn-block">+</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Calculator",
        data: function() {
            return {
                currentExpression: '',
                result: '',
                previousAnswer: ''
            }
        },
        methods: {
            press (x) {
                this.currentExpression += x;
            },
            clear() {
                this.currentExpression = '';
            },
            backspace() {
                this.currentExpression = this.currentExpression.substring(0, this.currentExpression.length - 1);
            },
            calculate(expression) {
                try {
                    let result = eval(expression);
                    this.result = result;
                    this.previousAnswer = result;

                } catch (e) {
                    if (e instanceof SyntaxError) {
                        this.result = "Error";
                    }
                }
            },
            plus() {
                this.currentExpression += '+';
            },
            minus() {
                this.currentExpression += '-';
            },
            multiply() {
                this.currentExpression += '*';
            },
            divide() {
                this.currentExpression += '/';
            },
            leftBracket() {
                this.currentExpression += '(';
            },
            rightBracket() {
                this.currentExpression += ')';
            },
            period() {
                this.currentExpression += '.';
            },
            getPreviousAnswer() {
                this.currentExpression += this.previousAnswer;
            }
        }
    }
</script>

<style scoped>
    .container {
        background-color: lightgray;
        padding-top: 5px;
        padding-bottom: 5px;
        max-width: 600px;
    }

    .row {
        padding-bottom: 8px;
    }

    #input {
        background-color: white;
        margin-bottom: 10px;
        margin-top: 5px;
        min-height: 50px;
        font-size: 30px;
    }

    #resultField {
        min-height: 50px;
        font-size: 30px;
    }

    button {
        border-color: black;
        padding: 10px 10px;
    }
</style>
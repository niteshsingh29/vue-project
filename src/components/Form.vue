<template>
    <div class="formAlign">
        <h1 :style="styleObject">{{ title }}</h1>
        <div class="form" :class="heading">
            <div class="abc">
                <label for="name" :style="labelStyling">Name - </label>
                <input v-model="name" type="text" placeholder="Enter your Name">
            </div>

            <div class="abc">
                <label for="name" :style="labelStyling">Date - </label>
                <select v-model="date.selectedDate">
                    <option disabled value="">Selct Date</option>
                    <option v-for="i in 31">{{ i }}</option>
                </select>
            </div>
            <div class="abc">
                <label for="name" :style="labelStyling">Month - </label>
                <select v-model="date.selectedMonth">
                    <option disabled value="">Selct Month</option>
                    <option v-for="month in months">{{ month }}</option>
                </select>
            </div>
            <div class="abc">
                <label for="name" :style="labelStyling">Year - </label>
                <select v-model="date.selectedYear">
                    <option disabled value="">Selct Year</option>
                    <option v-for="year in years">{{ year }}</option>
                </select>
            </div>

        </div>
        <button v-bind:disabled="isDisabled" @click="handleCalculate" :style="buttonStyle">Calculate
            Age</button>
        <h1 v-if="!isHeading">Hurray! your Age is ------> {{ age }}</h1>
        <button v-if="!isHeading" @click="handleReset" :style="buttonRStyle">Reset</button>
    </div>
</template>


<script>
export default {
    name: "Form",
    data() {
        return {
            title: "Simple Age Calculator",
            welcomeMsg: "Welcome to Vuejs World",
            isHeading: true,
            name: '',
            date: {
                selectedMonth: '',
                selectedDate: '',
                selectedYear: ''
            },
            months: ["jan", "feb", "mar", "apr", "may", "jun", "jul", "aug", "sep", "oct", "nov", "dec"],
            age: '',
            isDisabled: false
        }
    },
    computed: {
        styleObject() {
            return {
                color: "blue",
                'font-size': "50px",
                'margin': "10px 0px 10px 0px",
            }
        },
        labelStyling() {
            return {
                color: "black",
            }
        },
        heading() {
            return {
                heading: this.isHeading,
                altHeading: !this.isHeading
            }
        },
        buttonStyle() {
            return {
                'background-color': "black",
                color: "white",
                'margin': "20px 0px 20px 0px",
                cursor: "pointer"
            }
        },
        years() {
            const year = new Date().getFullYear();
            return Array.from({ length: year - 1979 }, (value, index) => 1980 + index)
        },
        buttonRStyle() {
            return {
                'background-color': "red",
                color: "black",
                'margin': "20px 0px 20px 0px",
                cursor: "pointer"
            }
        },

    },
    methods: {
        handleCalculate() {
            if (this.name === "" || this.date.selectedDate === "" || this.date.selectedMonth === "" || this.date.selectedYear === "") {
                alert("Please fill All details!")
            } else if (this.name !== "" && this.date.selectedDate !== "" && this.date.selectedMonth !== "" && this.date.selectedYear !== "") {
                let currentYear = 2022
                let finalAge = currentYear - this.date.selectedYear;
                return {
                    isHeading: this.isHeading ? this.isHeading = false : this.isHeading = true,
                    age: this.age = finalAge,
                    isDisabled: this.isDisabled = true,
                }
            }

        },
        handleReset() {
            return {
                name: this.name = '',
                date: {
                    selectedMonth: this.date.selectedMonth = '',
                    selectedDate: this.date.selectedDate = '',
                    selectedYear: this.date.selectedYear = '',
                },
                age: this.age = '',
                isHeading: this.isHeading ? this.isHeading = false : this.isHeading = true,
                isDisabled: this.isDisabled = false,

            }
        }
    }


}
</script>


<style scoped>
* {
    margin: 0;
    padding: 0;
    color: red;
    font-size: medium;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    height: 100%;
    min-height: 250px;
    align-items: flex-start;
}

.heading {
    background-color: greenyellow;
}

.altHeading {
    background-color: orange;
}

.formAlign {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
</style>

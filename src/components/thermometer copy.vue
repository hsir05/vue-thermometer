<template>
    <div class="warm-bg">
        <div class="thermometer">
            <div class="thermometer-body">
                <div class="thermometer-body-fill"></div>
            </div>
            <div class="thermometer-base">
                <div class="thermometer-base-fill"></div>
            </div>
            <div class="controls">
                <button id="very-hot" class="btn very-hot" aria-label="Set temperature to very hot">
                    <i class="fa-solid fa-fire-flame-curved fa-xl"></i>
                </button>
                <button id="hot" class="btn hot" aria-label="Set temperature to hot">
                    <i class="fa-solid fa-sun fa-xl"></i>
                </button>
                <button id="warm" class="btn warm" aria-label="Set temperature to warm">
                    <i class="fa-solid fa-cloud fa-xl"></i>
                </button>
                <button id="cold" class="btn cold" aria-label="Set temperature to cold">
                    <i class="fa-solid fa-snowflake fa-xl"></i>
                </button>
                <button id="very-cold" class="btn very-cold" aria-label="Set temperature to very cold">
                    <i class="fa-solid fa-icicles fa-xl"></i>
                </button>
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'

const FILL_HEIGHT = {
	"very-hot": "11px",
	hot: "90px",
	warm: "160px",
	cold: "230px",
	"very-cold": "300px"
};

let tempFill = document.querySelector(".thermometer-body-fill");
let controls = document.querySelector(".controls");

// controls.addEventListener("click", (event) => {
// 	if (event.target.nodeName === "BUTTON") {
// 		document.body.className = `${event.target.id}-bg`;
// 		tempFill.style.setProperty("top", FILL_HEIGHT[event.target.id]);
// 	}
// });


</script>


<style scoped>
html {
	width: 100vw;
	height: 100vh;
}

h1 {
	font-size: 22px;
	font-family: sans-serif;
	text-align: center;
	margin-bottom: 5px;
}

.thermometer {
	width: 200px;
	margin: 0 auto;
	position: relative;
}

.thermometer-base,
.thermometer-body {
	background-color: #ededfa;
	border: 15px solid #d8d9e8;
	margin: 0 auto;
}

.thermometer-base,
.thermometer-base-fill {
	margin: 0 auto;
	border-radius: 50%;
	z-index: 0;
}

.thermometer-base {
	height: 120px;
	width: 120px;
}

.thermometer-base::before {
	content: "";
	background-color: #db1d1d;
	height: 15px;
	width: 40px;
	position: absolute;
	left: 80px;
	z-index: 1;
}

.thermometer-base-fill {
	background-color: #db1d1d;
	height: 98px;
	width: 98px;
	position: relative;
	top: 11px;
	transition: top 0.5s cubic-bezier(0.33, 1, 0.68, 1);
}

.thermometer-body,
.thermometer-body-fill {
	margin: 0 auto;
	border-radius: 50px 50px 0 0;
	z-index: 1;
}

.thermometer-body {
	height: 325px;
	width: 60px;
	border-bottom: 0;
	position: relative;
	bottom: -23px;
	overflow: hidden;
}

.thermometer-body-fill {
	background-color: #db1d1d;
	height: 320px;
	width: 40px;
	position: relative;
	top: 160px; /* lowest value is 11px - highest value is 300px */
	transition: top 0.5s linear;
}

.controls {
	text-align: center;
	position: absolute;
	top: 38px;
	right: -40px;
	overflow: visible;
}

.btn {
	color: #2d2930;
	background-color: #dbdbdb;
	padding: 5px;
	height: 45px;
	width: 45px;
	margin-bottom: 30px;
	border-radius: 50%;
	border: none;
	filter: drop-shadow(3px 3px 4px #333333);
	box-shadow: inset 3px 3px 5px #fff;
	position: relative;
	display: block;
	cursor: pointer;
	transition: transform 0.2s linear;
}

.btn:hover {
	transform: scale(1.15);
}

i {
	pointer-events: none;
}

.very-hot-bg {
	background: rgb(232, 154, 30);
	background: linear-gradient(
		0deg,
		rgba(232, 154, 30, 1) 0%,
		rgba(232, 141, 30, 1) 35%,
		rgba(232, 50, 30, 1) 100%
	);
}

.hot-bg {
	background: rgb(229, 232, 30);
	background: linear-gradient(
		0deg,
		rgba(229, 232, 30, 1) 0%,
		rgba(232, 211, 30, 1) 35%,
		rgba(232, 154, 30, 1) 100%
	);
}

.warm-bg {
	background: rgb(30, 232, 52);
	background: linear-gradient(
		0deg,
		rgba(30, 232, 52, 1) 0%,
		rgba(151, 232, 30, 1) 35%,
		rgba(229, 232, 30, 1) 100%
	);
}

.cold-bg {
	background: rgb(30, 212, 232);
	background: linear-gradient(
		0deg,
		rgba(30, 212, 232, 1) 0%,
		rgba(30, 232, 130, 1) 35%,
		rgba(30, 232, 52, 1) 100%
	);
}

.very-cold-bg {
	background: rgb(120, 30, 232);
	background: linear-gradient(
		0deg,
		rgba(120, 30, 232, 1) 0%,
		rgba(30, 127, 232, 1) 35%,
		rgba(30, 212, 232, 1) 100%
	);
}

</style>

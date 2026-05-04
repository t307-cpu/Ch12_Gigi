<!DOCTYPE html> 
<html lang="en"> 
<head> 
<meta charset="UTF-8"> 
<meta name="viewport" content="width=device-width, initial-scale=1.0"> <title>Flowering Plant Reproduction Simulator</title> 
<style> 
* { 
font-family: Arial, sans-serif; 
margin: 0; 
padding: 0; box-sizing: border-box; 
} 
body { 
background-color: #f0f8f0; 
padding: 30px; 
max-width: 900px; 
margin: 0 auto; 
} 
.container { 
background: white; 
padding: 40px; 
border-radius: 12px; 
box-shadow: 0 0 15px #ccc; 
} 
h1 { 
color: #2e7d32; 
text-align: center; 
margin-bottom: 25px; 
} 
.content { 
font-size: 18px; 
line-height: 1.8; 
color: #333; 
margin-bottom: 30px; 
} 
.concept-check { 
background-color: #e8f5e9; 
padding: 15px; 
border-left: 5px solid #2e7d32; 
margin: 20px 0; 
border-radius: 6px; 
} 
.btn-container { 
display: flex;
gap: 15px; 
flex-wrap: wrap; 
justify-content: center; 
margin-top: 20px; 
} 
button { 
padding: 12px 25px; 
font-size: 16px; 
border: none; 
border-radius: 8px; 
background: #388e3c; 
color: white; 
cursor: pointer; 
transition: 0.3s; 
} 
button:hover { 
background: #2e7d32; 
} 
.hidden { 
display: none; 
} 
</style> 
</head> 
<body> 
<div class="container"> 
<h1>Plant Reproduction Life Cycle Simulator</h1> 
<!-- Scene 1: Reproduction Choice --> 
<div id="scene1" class="scene"> 
<div class="content"> 
Welcome to the Flowering Plant Reproduction Simulator! 
<br><br> 
A flowering plant must choose its method of reproduction to ensure species survival. <br><br> 
Choose your reproductive path: 
</div> 
<div class="btn-container"> 
<button onclick="goAsexual()">Path A: Asexual Reproduction</button> <button onclick="goSexual()">Path B: Sexual Reproduction</button> 
</div> 
</div> 
<!-- Scene 2: Asexual Reproduction Path --> 
<div id="asexualScene" class="scene hidden">
<div class="content"> 
<strong>Asexual Reproduction Selected</strong> 
<br><br> 
This reproductive method only involves <strong>mitotic cell division</strong>. <div class="concept-check"> 
<strong>Concept Check:</strong> No fusion of male and female gametes occurs. Offspring are genetically identical clones of the parent plant. 
</div> 
Asexual reproduction allows fast population growth with no need for pollinators. </div> 
<div class="btn-container"> 
<button onclick="restartGame()">Restart Simulation</button> 
</div> 
</div> 
<!-- Scene 3: Sexual Reproduction Intro --> 
<div id="sexualIntroScene" class="scene hidden"> 
<div class="content"> 
<strong>Sexual Reproduction Selected</strong> 
<br><br> 
This path involves the fusion of male and female gametes, which are produced through <strong>meiosis</strong>. 
<br><br> 
Next step: Choose your pollination type. 
</div> 
<div class="btn-container"> 
<button onclick="selfPollination()">Self-Pollination</button> 
<button onclick="crossPollination()">Cross-Pollination</button> 
</div> 
</div> 
<!-- Scene 4: Self Pollination --> 
<div id="selfPollScene" class="scene hidden"> 
<div class="content"> 
<strong>Self-Pollination</strong> 
<br><br> 
Pollen transfers within the same flower or same individual plant. 
<div class="concept-check"> 
<strong>Genetic Variation Note:</strong> Self-pollination creates <strong>less genetic variation</strong>. This limits the plant’s ability to adapt to sudden environmental changes. 
</div> 
Move on to fertilization and fruit/seed formation. 
</div>
<div class="btn-container"> 
<button onclick="fertilizationPhase()">Continue to Fertilization</button> </div> 
</div> 
<!-- Scene 5: Cross Pollination --> 
<div id="crossPollScene" class="scene hidden"> 
<div class="content"> 
<strong>Cross-Pollination</strong> 
<br><br> 
Pollen transfers between two different individual plants of the same species. <div class="concept-check"> 
<strong>Genetic Variation Note:</strong> Cross-pollination creates 
<strong>greater genetic variation</strong>. This increases the species chance of survival in changing environments. 
</div> 
Move on to fertilization and fruit/seed formation. 
</div> 
<div class="btn-container"> 
<button onclick="fertilizationPhase()">Continue to Fertilization</button> </div> 
</div> 
<!-- Scene 6: Fertilization & Transformation --> 
<div id="fertilizationScene" class="scene hidden"> 
<div class="content"> 
<strong>Fertilization & Structural Transformation</strong> 
<br><br> 
Pollen grains land on the stigma and grow a <strong>pollen tube</strong> down through the style to reach the ovule. 
<br><br> 
Male gametes travel down the pollen tube to fuse with the female egg cell. <div class="concept-check"> 
<strong>Plant Part Transformation:</strong><br> 
• Ovule → Develops into Seed<br> 
• Ovary → Develops into Fruit 
</div> 
Next: Choose a seed dispersal method. 
</div> 
<div class="btn-container"> 
<button onclick="seedDispersal('wind')">Wind Dispersal</button> 
<button onclick="seedDispersal('water')">Water Dispersal</button> 
<button onclick="seedDispersal('animal')">Animal Dispersal</button> </div>
</div> 
<!-- Scene 7: Seed Dispersal Final --> 
<div id="dispersalScene" class="scene hidden"> 
<div class="content" id="dispersalText"></div> 
<div class="concept-check"> 
<strong>Why Seed Dispersal Is Vital:</strong><br> 
1. Prevents overcrowding and competition for light, water, and minerals with the parent plant.<br> 
2. Allows the plant species to colonize new habitats and expand its range. </div> 
<div class="btn-container"> 
<button onclick="restartGame()">Play Again</button> 
</div> 
</div> 
</div> 
<script> 
// Hide all scenes 
function hideAllScenes() { 
const scenes = document.querySelectorAll('.scene'); 
scenes.forEach(scene => scene.classList.add('hidden')); 
} 
// Start Asexual Reproduction 
function goAsexual() { 
hideAllScenes(); 
document.getElementById('asexualScene').classList.remove('hidden'); } 
// Start Sexual Reproduction 
function goSexual() { 
hideAllScenes(); 
document.getElementById('sexualIntroScene').classList.remove('hidden'); } 
// Self Pollination 
function selfPollination() { 
hideAllScenes(); 
document.getElementById('selfPollScene').classList.remove('hidden'); } 
// Cross Pollination
function crossPollination() { 
hideAllScenes(); 
document.getElementById('crossPollScene').classList.remove('hidden'); } 
// Fertilization Phase 
function fertilizationPhase() { 
hideAllScenes(); 
document.getElementById('fertilizationScene').classList.remove('hidden'); } 
// Seed Dispersal Result 
function seedDispersal(type) { 
hideAllScenes(); 
let text = ""; 
if(type === "wind"){ 
text = "<strong>Wind Seed Dispersal</strong><br>Light seeds with wing-like structures are carried by wind to new locations."; 
} else if(type === "water"){ 
text = "<strong>Water Seed Dispersal</strong><br>Buoyant, waterproof seeds float along rivers and oceans to new land areas."; 
} else if(type === "animal"){ 
text = "<strong>Animal Seed Dispersal</strong><br>Seeds with hooks or fleshy fruit stick to animal fur or are eaten and excreted in new places."; 
} 
document.getElementById('dispersalText').innerHTML = text; 
document.getElementById('dispersalScene').classList.remove('hidden'); } 
// Restart Game 
function restartGame() { 
hideAllScenes(); 
document.getElementById('scene1').classList.remove('hidden'); 
} 
</script> 
</body> 
</html>

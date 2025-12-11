<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Matching Game</title>
<style>
  body { font-family: Arial, sans-serif; padding: 20px; background: #f4f4f4; }
  h1 { text-align: center; }
  .container { display: flex; gap: 40px; justify-content: center; }
  .terms, .definitions { width: 45%; }
  .item { background: white; padding: 10px; margin: 8px 0; border: 1px solid #ccc; border-radius: 6px; cursor: grab; }
  .dropzone { background: #e7e7e7; padding: 10px; min-height: 40px; border: 2px dashed #bbb; border-radius: 6px; margin: 8px 0; }
  .correct { background: #c8ffc8 !important; }
  .wrong { background: #ffb8b8 !important; }
  button { padding: 10px 15px; margin-top: 20px; font-size: 16px; cursor: pointer; }
</style>
</head>
<body>
<h1>Drag & Drop Matching Game</h1>
<p>Drag each term on the left to its correct definition on the right.</p>

<div class="container">
  <div class="terms">
    <h2>Terms</h2>
    <div class="item" draggable="true" id="actuating">Actuating</div>
    <div class="item" draggable="true" id="communication_climate">Communication climate</div>
    <div class="item" draggable="true" id="confirming_response">Confirming response</div>
    <div class="item" draggable="true" id="dialectical_model">Dialectical model</div>
    <div class="item" draggable="true" id="affinity">Affinity</div>
    <div class="item" draggable="true" id="escalatory_conflict_spiral">Escalatory conflict spiral</div>
    <div class="item" draggable="true" id="gibb_categories">Gibb categories</div>
    <div class="item" draggable="true" id="groupthink">Groupthink</div>
    <div class="item" draggable="true" id="information_hunger">Information hunger</div>
    <div class="item" draggable="true" id="metacommunication">Metacommunication</div>
    <div class="item" draggable="true" id="motivated_sequence">Motivated sequence</div>
    <div class="item" draggable="true" id="nominal_group_technique">Nominal group technique</div>
    <div class="item" draggable="true" id="disclosure">Disclosure</div>
    <div class="item" draggable="true" id="passive_aggression">Passive aggression</div>
    <div class="item" draggable="true" id="procedural_norms">Procedural norms</div>
    <div class="item" draggable="true" id="relational_message">Relational message</div>
    <div class="item" draggable="true" id="self_disclosure">Self-disclosure</div>
    <div class="item" draggable="true" id="task_orientation">Task orientation</div>
    <div class="item" draggable="true" id="testimony">Testimony</div>
    <div class="item" draggable="true" id="topic_pattern">Topic pattern</div>
  </div>

  <div class="definitions">
    <h2>Definitions</h2>
    <div class="dropzone" data-answer="actuating">Final action stage in the motivated sequence.</div>
    <div class="dropzone" data-answer="communication_climate">Emotional tone of a relationship created by communication.</div>
    <div class="dropzone" data-answer="confirming_response">Message showing value and recognition of another person.</div>
    <div class="dropzone" data-answer="dialectical_model">Tension between opposing relational needs.</div>
    <div class="dropzone" data-answer="affinity">Positive feelings of liking toward someone.</div>
    <div class="dropzone" data-answer="escalatory_conflict_spiral">A cycle where conflict keeps getting worse.</div>
    <div class="dropzone" data-answer="gibb_categories">Supportive vs. defensive communication behaviors.</div>
    <div class="dropzone" data-answer="groupthink">Group suppression of disagreement to maintain unity.</div>
    <div class="dropzone" data-answer="information_hunger">Motivation created by wanting information.</div>
    <div class="dropzone" data-answer="metacommunication">Communication about communication.</div>
    <div class="dropzone" data-answer="motivated_sequence">Five-step persuasive pattern.</div>
    <div class="dropzone" data-answer="nominal_group_technique">Silent idea generation before discussion.</div>
    <div class="dropzone" data-answer="disclosure">Sharing personal information.</div>
    <div class="dropzone" data-answer="passive_aggression">Indirect, hostile behavior that avoids direct confrontation.</div>
    <div class="dropzone" data-answer="procedural_norms">Rules for how a group operates and makes decisions.</div>
    <div class="dropzone" data-answer="relational_message">Message expressing how people feel about the relationship.</div>
    <div class="dropzone" data-answer="self_disclosure">Intentionally revealing private personal information.</div>
    <div class="dropzone" data-answer="task_orientation">Focus on accomplishing group goals.</div>
    <div class="dropzone" data-answer="testimony">Using experience or statements as evidence in speeches.</div>
    <div class="dropzone" data-answer="topic_pattern">Organizing a speech by categories or subjects.</div>
  </div>
</div>

<button onclick="checkAnswers()">Check Answers</button>

<script>
let draggedItem = null;

document.querySelectorAll('.item').forEach(item => {
  item.addEventListener('dragstart', () => {
    draggedItem = item;
  });
});

document.querySelectorAll('.dropzone').forEach(zone => {
  zone.addEventListener('dragover', e => e.preventDefault());
  zone.addEventListener('drop', () => {
    if (draggedItem) {
      zone.innerHTML = '';
      zone.appendChild(draggedItem);
    }
  });
});

function checkAnswers() {
  document.querySelectorAll('.dropzone').forEach(zone => {
    const correct = zone.dataset.answer;
    if (zone.firstElementChild && zone.firstElementChild.id === correct) {
      zone.classList.add('correct');
      zone.classList.remove('wrong');
    } else {
      zone.classList.add('wrong');
      zone.classList.remove('correct');
    }
  });
}
</script>

</body>
</html>

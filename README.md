<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Communication compass questionnaire</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .question {
            margin: 15px 0;
        }
        .result {
            font-size: 1.2em;
            font-weight: bold;
            color: #333;
            margin-top: 20px;
        }
        button {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 1em;
        }
    </style>
</head>
<body>

<h1>Communication Compass Questionnaire</h1>
<p>For each question, choose either A or B based on what feels more natural to you.</p>

<form id="quizForm">
    <!-- Questions -->
    <div class="question">
        <label>1. When giving feedback, how do you prefer to communicate?</label><br>
        <input type="radio" name="q1" value="A" required> A. Direct and to the point<br>
        <input type="radio" name="q1" value="B"> B. Diplomatic and careful with words
    </div>
    <div class="question">
        <label>2. When discussing a project, what’s your focus?</label><br>
        <input type="radio" name="q2" value="A" required> A. Overall vision and goals<br>
        <input type="radio" name="q2" value="B"> B. Details and execution
    </div>
    <div class="question">
        <label>3. In meetings, how do you express your ideas?</label><br>
        <input type="radio" name="q3" value="A" required> A. Clearly and concisely<br>
        <input type="radio" name="q3" value="B"> B. Indirectly, suggesting things
    </div>
    <div class="question">
        <label>4. When working on a problem, what’s your first instinct?</label><br>
        <input type="radio" name="q4" value="A" required> A. Big picture and main objectives<br>
        <input type="radio" name="q4" value="B"> B. Break it down into steps
    </div>
    <div class="question">
        <label>5. How do you prefer to receive feedback?</label><br>
        <input type="radio" name="q5" value="A" required> A. Clear and direct<br>
        <input type="radio" name="q5" value="B"> B. Gentle and considerate
    </div>
    <div class="question">
        <label>6. When planning a project, what’s most important to you?</label><br>
        <input type="radio" name="q6" value="A" required> A. High-level strategy and vision<br>
        <input type="radio" name="q6" value="B"> B. Detailed tasks and timeline
    </div>
    <div class="question">
        <label>7. How do you handle disagreement in a conversation?</label><br>
        <input type="radio" name="q7" value="A" required> A. Directly address and discuss<br>
        <input type="radio" name="q7" value="B"> B. Approach carefully, avoid conflict
    </div>
    <div class="question">
        <label>8. What’s your preferred communication style in a group setting?</label><br>
        <input type="radio" name="q8" value="A" required> A. Straightforward and efficient<br>
        <input type="radio" name="q8" value="B"> B. Thoughtful and measured
    </div>
    <div class="question">
        <label>9. How do you explain ideas to others?</label><br>
        <input type="radio" name="q9" value="A" required> A. Overview and end goal<br>
        <input type="radio" name="q9" value="B"> B. Step-by-step explanation
    </div>
    <div class="question">
        <label>10. When presenting information, what’s your approach?</label><br>
        <input type="radio" name="q10" value="A" required> A. Main points and outcomes<br>
        <input type="radio" name="q10" value="B"> B. Details and process
    </div>

    <button type="button" onclick="calculateResult()">Submit</button>
</form>

<div class="result" id="result"></div>

<script>
    function calculateResult() {
        // Get all form inputs
        const form = document.forms['quizForm'];
        let directCount = 0, bigPictureCount = 0;

        // Direct vs. Indirect questions
        if (form.q1.value === "A") directCount++;
        if (form.q3.value === "A") directCount++;
        if (form.q5.value === "A") directCount++;
        if (form.q7.value === "A") directCount++;
        if (form.q8.value === "A") directCount++;

        // Big Picture vs. Detail-Oriented questions
        if (form.q2.value === "A") bigPictureCount++;
        if (form.q4.value === "A") bigPictureCount++;
        if (form.q6.value === "A") bigPictureCount++;
        if (form.q9.value === "A") bigPictureCount++;
        if (form.q10.value === "A") bigPictureCount++;

        // Determine the quadrant
        let resultText = '';
        if (directCount >= 3 && bigPictureCount >= 3) {
            resultText = "You are Direct & Big Picture.";
        } else if (directCount >= 3 && bigPictureCount < 3) {
            resultText = "You are Direct & Detail-Oriented.";
        } else if (directCount < 3 && bigPictureCount >= 3) {
            resultText = "You are Indirect & Big Picture.";
        } else {
            resultText = "You are Indirect & Detail-Oriented.";
        }

        // Display the result
        document.getElementById('result').textContent = resultText;
    }
</script>

</body>
</html>

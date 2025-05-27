# CSS3 Transitions, Animations, and Advanced JavaScript Functions

  <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>CSS Animation ,localStorage ,JS</title>
<style>
  body {
    font-family: Arial, sans-serif;
    transition: background-color 0.5s ease;
  }

  /* Button style */
  #animateBtn {
    padding: 15px 30px;
    font-size: 18px;
    background-color: #3498db;
    border: none;
    color: white;
    cursor: pointer;
    border-radius: 6px;
    outline: none;
  }

  /* CSS animation */
  @keyframes buttonPulse {
    0% {
      transform: scale(1);
      background-color: #3498db;
    }
    50% {
      transform: scale(1.1);
      background-color: #2980b9;
    }
    100% {
      transform: scale(1);
      background-color: #3498db;
    }
  }

  /* Class to trigger animation */
  .pulse {
    animation: buttonPulse 0.6s ease forwards;
  }
</style>
</head>
<body>

<h2>User Preference & Animation Demo</h2>

<button id="animateBtn">Click Me!</button>

<script>
  const button = document.getElementById('animateBtn');

  function saveUserPreference(color) {
    localStorage.setItem('preferredBgColor', color);
  }

  
  function applyUserPreference() {
    const savedColor = localStorage.getItem('preferredBgColor');
    if (savedColor) {
      document.body.style.backgroundColor = savedColor;
    }
  }


  function animateAndStorePreference() {
    
    button.classList.add('pulse');

   
    button.addEventListener('animationend', () => {
      button.classList.remove('pulse');
    }, { once: true });

    
    const currentColor = document.body.style.backgroundColor;
    const newColor = currentColor === 'rgb(231, 76, 60)' ? '#2ecc71' : '#e74c3c';

    document.body.style.backgroundColor = newColor;

   
    saveUserPreference(newColor);
  }

  
  button.addEventListener('click', animateAndStorePreference);

  
</script>

</body>
</html>


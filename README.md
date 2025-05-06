# week6html-assign

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>JavaScript Playground</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <h1>JavaScript Playground 🎉</h1>

  <!-- Event Handling Section -->
  <section id="event-handling">
    <h2>1. Event Handling 🎈</h2>
    <button id="click-btn">Click me!</button>
    <div id="hover-box">Hover over me!</div>
    <input type="text" id="keypress-input" placeholder="Type something..." />
    <p id="keypress-output"></p>
  </section>

  <!-- Interactive Elements Section -->
  <section id="interactive-elements">
    <h2>2. Interactive Elements 🎮</h2>

    <!-- Button that changes text/color -->
    <button id="color-btn">Change my color & text</button>

    <!-- Simple Image Gallery -->
    <div id="gallery">
      <img id="gallery-img" src="https://picsum.photos/id/1015/400/250" alt="Gallery Image" />
      <br />
      <button id="prev-img">Previous</button>
      <button id="next-img">Next</button>
    </div>

    <!-- Accordion -->
    <div class="accordion">
      <button class="accordion-btn">Section 1</button>
      <div class="accordion-content">
        <p>This is content for section 1.</p>
      </div>

      <button class="accordion-btn">Section 2</button>
      <div class="accordion-content">
        <p>This is content for section 2.</p>
      </div>

      <button class="accordion-btn">Section 3</button>
      <div class="accordion-content">
        <p>This is content for section 3.</p>
      </div>
    </div>
  </section>

  <!-- Form Validation Section -->
  <section id="form-validation">
    <h2>3. Form Validation 📋✅</h2>
    <form id="signup-form" novalidate>
      <label>
        Name (required):
        <input type="text" id="name" required />
        <span class="error" id="name-error"></span>
      </label>
      <br />

      <label>
        Email (required):
        <input type="email" id="email" required />
        <span class="error" id="email-error"></span>
      </label>
      <br />

      <label>
        Password (min 8 chars):
        <input type="password" id="password" required />
        <span class="error" id="password-error"></span>
      </label>
      <br />

      <button type="submit">Sign Up</button>
    </form>
  </section>

  <script src="script.js"></script>
</body>
</html>


css sytle

body {
  font-family: Arial, sans-serif;
  max-width: 700px;
  margin: 2rem auto;
  padding: 0 1rem;
  background: #f9f9f9;
  color: #333;
}

h1, h2 {
  text-align: center;
  color: #2c3e50;
}

button {
  cursor: pointer;
  padding: 0.5rem 1rem;
  margin: 0.5rem 0.3rem;
  border: none;
  border-radius: 4px;
  background-color: #3498db;
  color: white;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #2980b9;
}

#hover-box {
  width: 200px;
  height: 100px;
  background-color: #eee;
  border: 2px solid #ccc;
  line-height: 100px;
  text-align: center;
  margin: 1rem 0;
  user-select: none;
  transition: background-color 0.3s ease;
}

.accordion-btn {
  width: 100%;
  text-align: left;
  background-color: #34495e;
  color: white;
  padding: 0.7rem;
  border: none;
  outline: none;
  cursor: pointer;
  font-size: 1rem;
  margin-top: 0.5rem;
  border-radius: 4px;
  transition: background-color 0.3s ease;
}

.accordion-btn.active, .accordion-btn:hover {
  background-color: #2c3e50;
}

.accordion-content {
  background-color: white;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease;
  padding: 0 1rem;
  border-left: 2px solid #34495e;
  border-right: 2px solid #34495e;
  border-bottom: 2px solid #34495e;
  border-radius: 0 0 4px 4px;
}

.error {
  color: red;
  font-size: 0.9rem;
  margin-left: 0.5rem;
}

input[type="text"],
input[type="email"],
input[type="password"] {
  padding: 0.4rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-left: 0.3rem;
  width: 200px;
}

input:invalid {
  border-color: red;
}

#gallery {
  text-align: center;
  margin: 1rem 0;
}

#gallery-img {
  width: 100%;
  max-width: 400px;
  border-radius: 8px;
  transition: transform 0.4s ease;
}

#gallery-img.animate {
  transform: scale(1.05);
}


js script

// ===== 1. Event Handling =====

// Button click
const clickBtn = document.getElementById('click-btn');
clickBtn.addEventListener('click', () => {
  alert('You clicked the button! 🎉');
});

// Hover effects
const hoverBox = document.getElementById('hover-box');
hoverBox.addEventListener('mouseenter', () => {
  hoverBox.style.backgroundColor = '#3498db';
  hoverBox.style.color = 'white';
});
hoverBox.addEventListener('mouseleave', () => {
  hoverBox.style.backgroundColor = '#eee';
  hoverBox.style.color = 'black';
});

// Keypress detection
const keypressInput = document.getElementById('keypress-input');
const keypressOutput = document.getElementById('keypress-output');
keypressInput.addEventListener('keydown', (e) => {
  keypressOutput.textContent = `You pressed: "${e.key}" (code: ${e.code})`;
});

// Bonus: Secret action on double-click or long press
clickBtn.addEventListener('dblclick', () => {
  alert('Secret double-click action unlocked! 🤫');
});

// Long press detection for hoverBox (press 1.5s)
let pressTimer;
hoverBox.addEventListener('mousedown', () => {
  pressTimer = setTimeout(() => {
    alert('Long press detected! Secret hover box action! 🤫');
  }, 1500);
});
hoverBox.addEventListener('mouseup', () => clearTimeout(pressTimer));
hoverBox.addEventListener('mouseleave', () => clearTimeout(pressTimer));


// ===== 2. Interactive Elements =====

// Button that changes text and color
const colorBtn = document.getElementById('color-btn');
colorBtn.addEventListener('click', () => {
  const colors = ['#e74c3c', '#27ae60', '#8e44ad', '#f39c12', '#16a085'];
  const randomColor = colors[Math.floor(Math.random() * colors.length)];
  colorBtn.style.backgroundColor = randomColor;
  colorBtn.textContent = `Color changed to ${randomColor}`;
});

// Image gallery/slideshow
const galleryImages = [
  'https://picsum.photos/id/1015/400/250',
  'https://picsum.photos/id/1016/400/250',
  'https://picsum.photos/id/1018/400/250',
  'https://picsum.photos/id/1020/400/250',
];
let currentImageIndex = 0;

const galleryImg = document.getElementById('gallery-img');
const prevImgBtn = document.getElementById('prev-img');
const nextImgBtn = document.getElementById('next-img');

function updateGalleryImage() {
  galleryImg.classList.remove('animate');
  void galleryImg.offsetWidth; // trigger reflow for animation restart
  galleryImg.src = galleryImages[currentImageIndex];
  galleryImg.classList.add('animate');
}

prevImgBtn.addEventListener('click', () => {
  currentImageIndex =
    (currentImageIndex - 1 + galleryImages.length) % galleryImages.length;
  updateGalleryImage();
});

nextImgBtn.addEventListener('click', () => {
  currentImageIndex = (currentImageIndex + 1) % galleryImages.length;
  updateGalleryImage();
});

// Accordion
const accordionBtns = document.querySelectorAll('.accordion-btn');
accordionBtns.forEach((btn) => {
  btn.addEventListener('click', () => {
    btn.classList.toggle('active');
    const content = btn.nextElementSibling;
    if (content.style.maxHeight) {
      content.style.maxHeight = null;
    } else {
      // Close others
      document.querySelectorAll('.accordion-content').forEach((c) => {
        c.style.maxHeight = null;
        c.previousElementSibling.classList.remove('active');
      });
      content.style.maxHeight = content.scrollHeight + 'px';
      btn.classList.add('active');
    }
  });
});


// ===== 3. Form Validation =====

const form = document.getElementById('signup-form');

const nameInput = document.getElementById('name');
const emailInput = document.getElementById('email');
const passwordInput = document.getElementById('password');

const nameError = document.getElementById('name-error');
const emailError = document.getElementById('email-error');
const passwordError = document.getElementById('password-error');

// Helper validation functions
function validateName() {
  if (nameInput.value.trim() === '') {
    nameError.textContent = 'Name is required.';
    return false;
  }
  nameError.textContent = '';
  return true;
}

function validateEmail() {
  const email = emailInput.value.trim();
  // Simple email regex
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  if (email === '') {
    emailError.textContent = 'Email is required.';
    return false;
  } else if (!emailRegex.test(email)) {
    emailError.textContent = 'Please enter a valid email.';
    return false;
  }
  emailError.textContent = '';
  return true;
}

function validatePassword() {
  const pwd = passwordInput.value;
  if (pwd.length < 8) {
    passwordError.textContent = 'Password must be at least 8 characters.';
    return false;
  }
  passwordError.textContent = '';
  return true;
}

// Real-time feedback (bonus)
nameInput.addEventListener('input', validateName);
emailInput.addEventListener('input', validateEmail);
passwordInput.addEventListener('input', validatePassword);

form.addEventListener('submit', (e) => {
  e.preventDefault();

  const isNameValid = validateName();
  const isEmailValid = validateEmail();
  const isPasswordValid = validatePassword();

  if (isNameValid && isEmailValid && isPasswordValid) {
    alert('Form submitted successfully! 🎉');
    form.reset();
    // Clear errors
    nameError.textContent = '';
    emailError.textContent = '';
    passwordError.textContent = '';
  } else {
    alert('Please fix the errors before submitting.');
  }
});

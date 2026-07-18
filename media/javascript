document.addEventListener('DOMContentLoaded', function () {
    const courseButtons = document.querySelectorAll('.course-btn[data-course]');
    const courseSections = document.querySelectorAll('.course-content');
    const visitorDetails = document.getElementById('visitor-details');

    function trackVisitor() {
        if (!visitorDetails) {
            return;
        }

        const storedVisits = JSON.parse(localStorage.getItem('cybersecurity-visits') || '[]');
        const visit = {
            userAgent: navigator.userAgent || 'Unknown browser',
            platform: navigator.platform || 'Unknown platform',
            language: navigator.language || 'Unknown language',
            referrer: document.referrer || 'Direct visit',
            visitedAt: new Date().toLocaleString()
        };

        storedVisits.push(visit);
        localStorage.setItem('cybersecurity-visits', JSON.stringify(storedVisits.slice(-20)));

        visitorDetails.textContent = 'Browser: ' + visit.userAgent + ' | Platform: ' + visit.platform + ' | Visits recorded on this device: ' + storedVisits.length + ' | Last visit: ' + visit.visitedAt;
    }

    trackVisitor();

    function showCourse(courseId) {
        const selectedCourse = document.getElementById('course-' + courseId);

        courseSections.forEach(function (course) {
            course.style.display = 'none';
        });

        courseButtons.forEach(function (button) {
            button.classList.remove('active');
        });

        if (selectedCourse) {
            selectedCourse.style.display = 'block';
            selectedCourse.scrollIntoView({ behavior: 'smooth' });
        }

        const activeButton = document.querySelector('.course-btn[data-course="' + courseId + '"]');
        if (activeButton) {
            activeButton.classList.add('active');
        }
    }

    if (courseButtons.length > 0) {
        courseButtons.forEach(function (button) {
            button.addEventListener('click', function () {
                showCourse(button.dataset.course);
            });
        });
    }

    const submitButton = document.getElementById('submit-networking-quiz');
    const resultsBlock = document.getElementById('networking-results');
    const quizSection = document.getElementById('networking-quiz');

    if (submitButton && resultsBlock && quizSection) {
        submitButton.addEventListener('click', function () {
            const answerKey = resultsBlock.querySelector('.answer-key');
            resultsBlock.style.display = 'block';
            quizSection.classList.add('quiz-submitted');

            if (answerKey) {
                answerKey.open = true;
            }
        });
    }

    const loginForm = document.getElementById('login-form');
    if (loginForm) {
        loginForm.addEventListener('submit', function (event) {
            event.preventDefault();
            alert('Form validation passed! (Backend not yet implemented)');
        });
    }

    const signupForm = document.getElementById('signup-form');
    const passwordInput = document.getElementById('psw');
    const confirmPasswordInput = document.getElementById('confirmpassword');

    if (signupForm && passwordInput && confirmPasswordInput) {
        confirmPasswordInput.addEventListener('input', function () {
            if (confirmPasswordInput.value !== passwordInput.value) {
                confirmPasswordInput.setCustomValidity('Passwords do not match');
            } else {
                confirmPasswordInput.setCustomValidity('');
            }
        });

        signupForm.addEventListener('submit', function (event) {
            event.preventDefault();
            if (passwordInput.value !== confirmPasswordInput.value) {
                confirmPasswordInput.setCustomValidity('Passwords do not match');
                confirmPasswordInput.reportValidity();
                return;
            }
            window.location.href = 'login.html';
        });
    }
});

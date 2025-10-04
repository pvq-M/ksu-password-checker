<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>بوابة جامعة الملك سعود لأمن كلمات المرور</title>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700&display=swap" rel="stylesheet">
    
    <style>
        /* ------------------- الأنماط العامة والملاحة ------------------- */
        body {
            font-family: 'Tajawal', sans-serif;
            background-color: #f4f7f6;
            color: #333;
            direction: rtl; 
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
        }
        .tab-navigation {
            width: 100%;
            background-color: #004d40;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            position: sticky;
            top: 0;
            z-index: 100;
            display: flex;
            justify-content: center;
        }
        .tab-button {
            background: none;
            border: none;
            color: #ffffff;
            padding: 15px 25px;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            transition: background-color 0.3s;
            outline: none;
        }
        .tab-button.active {
            background-color: #007bff; 
            border-bottom: 3px solid #f39c12; 
        }

        /* التحكم في إظهار وإخفاء الأقسام */
        .page-content {
            display: none; 
            width: 100%;
            max-width: 900px; 
            background-color: #ffffff;
            padding: 40px 60px;
            margin-top: 20px;
            margin-bottom: 40px;
            border-radius: 12px;
            box-shadow: 0 6px 30px rgba(0, 0, 0, 0.1);
            box-sizing: border-box;
        }
        .page-content.active {
            display: block; 
        }

        h1, h2 {
            color: #004d40; 
            margin-bottom: 25px;
            font-weight: 700;
            text-align: center;
        }
        
        /* ------------------- 1. أنماط الواجهة الرئيسية ------------------- */
        .ksu-logo {
            width: 150px;
            height: auto;
            margin-bottom: 20px;
        }
        .importance-text {
            font-size: 1.1rem;
            line-height: 1.8;
            margin-bottom: 30px;
            text-align: justify;
        }
        
        /* ------------------- 2. أنماط اختبار كلمة السر (مُغلفة) ------------------- */
        /* التغيير الأساسي: وضع كل العناصر داخل غلاف واحد للتأكد من أنها لا تظهر إلا هنا */
        .test-section-wrapper { 
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center; /* توسيط النص داخل الحاوية */
            width: 100%; /* ضمان استخدام العرض الكامل */
        }
        .test-section-wrapper input {
            width: 80%;
            padding: 12px;
            font-size: 16px;
            margin-bottom: 15px;
            border: 2px solid #eee;
            border-radius: 8px;
            text-align: right;
            max-width: 400px; /* تحديد أقصى عرض لحقل الإدخال */
        }
        .strength-bar {
            height: 10px;
            border-radius: 8px;
            background: #e0e0e0;
            overflow: hidden;
            margin-bottom: 10px;
            width: 80%;
            max-width: 400px;
        }
        .bar { height: 100%; width: 0%; transition: width 0.4s ease, background-color 0.4s ease; }
        .very-weak { background: #e74c3c; } .weak { background: #f39c12; }
        .good { background: #2ecc71; } .strong { background: #1abc9c; }
        .strength-text {
            font-weight: bold;
            color: #555;
            min-height: 20px;
        }

        /* ------------------- 3. أنماط تواصل معنا ------------------- */
        .contact-info p {
            font-size: 1.1rem;
            margin: 15px 0;
            padding: 10px;
            border-bottom: 1px solid #eee;
        }
        .contact-info a {
            color: #007bff;
            text-decoration: none;
            font-weight: bold;
        }
    </style>
</head>
<body onload="switchTab('home')">

    <div class="tab-navigation">
        <button class="tab-button" data-section="home">الواجهة الرئيسية</button>
        <button class="tab-button" data-section="test">اختبار كلمة السر</button>
        <button class="tab-button" data-section="contact">تواصل معنا</button>
    </div>

    <div id="home" class="page-content home-section">
        <div class="header">
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c5/Ksu-logo-white-ar.svg/1200px-Ksu-logo-white-ar.svg.png" alt="شعار جامعة الملك سعود" class="ksu-logo" />
            <h1>بوابة التوعية بأمن كلمات المرور</h1>
        </div>
        <h2>💡 أهمية كلمة المرور القوية</h2>
        <p class="importance-text">
            هذا القسم مخصص للتعريف والتوعية. لا يحتوي على أي حقول لاختبار كلمة المرور.
        </p>
    </div>

    <div id="test" class="page-content test-section">
        <div class="test-section-wrapper">
            <h2>🔐 اختبار قوة كلمة المرور المُحسن</h2>
            <input type="password" id="password" placeholder="اكتب كلمة المرور هنا..." dir="auto" /> 
            
            <div class="strength-bar"><div class="bar" id="bar"></div></div>
            <div class="strength-text" id="strength-text">اكتب كلمة المرور لبدء الفحص</div>
        </div>
    </div>

    <div id="contact" class="page-content contact-section">
        <h2>📧 تواصل معنا</h2>
        <div class="contact-info">
            <p>هذا القسم مخصص للتواصل فقط. لا يحتوي على أي حقول لاختبار كلمة المرور.</p>
            <p>
                **الإيميل الأول:** <a href="mailto:email1@example.com">email1@example.com</a>
            </p>
            <p>
                **الإيميل الثاني:** <a href="mailto:email2@example.com">email2@example.com</a>
            </p>
            <p>
                **الإيميل الثالث:** <a href="mailto:email3@example.com">email3@example.com</a>
            </p>
        </div>
    </div>

    <script>
        // دالة التنقل بين الأقسام (الصفحات)
        function switchTab(sectionId) {
            document.querySelectorAll('.page-content').forEach(content => {
                content.classList.remove('active');
            });
            document.querySelectorAll('.tab-button').forEach(button => {
                button.classList.remove('active');
            });

            document.getElementById(sectionId).classList.add('active');
            document.querySelector(`.tab-button[data-section="${sectionId}"]`).classList.add('active');
        }

        // إضافة مستمعي الأحداث لأزرار التنقل
        document.querySelectorAll('.tab-button').forEach(button => {
            button.addEventListener('click', () => {
                switchTab(button.getAttribute('data-section'));
            });
        });

        // ------------------- كود اختبار قوة كلمة المرور -------------------
        const passwordInput = document.getElementById("password");
        const bar = document.getElementById("bar");
        const text = document.getElementById("strength-text");

        // يتم تشغيل هذا الكود فقط عندما تكون العناصر موجودة في الـ DOM
        if (passwordInput && bar && text) { 
            function updateStrengthUI(width, className, statusText) {
                bar.style.width = `${width}%`;
                bar.className = `bar ${className}`; 
                text.textContent = statusText;
            }

            passwordInput.addEventListener("input", () => {
                const value = passwordInput.value;
                let strength = 0; 

                // حساب القوة 
                if (value.length >= 12) { strength += 4; } else if (value.length >= 8) { strength += 2; } else if (value.length > 0) { strength += 1; }
                if (/[a-z]/.test(value) && /[A-Z]/.test(value)) strength += 2;
                if (/\d/.test(value)) strength += 1;
                if (/[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>\/?]/.test(value)) strength += 3;
                if (/(.)\1{2,}/.test(value)) strength -= 2; 
                
                // تحديد المستوى
                if (value.length === 0) {
                    updateStrengthUI(0, "", "اكتب كلمة المرور لبدء الفحص");
                } else if (strength < 4) {
                    updateStrengthUI(25, "very-weak", "ضعيفة جداً 🔴");
                } else if (strength < 7) {
                    updateStrengthUI(50, "weak", "ضعيفة 🟠");
                } else if (strength < 10) {
                    updateStrengthUI(75, "good", "جيدة 🟡");
                } else {
                    updateStrengthUI(100, "strong", "قوية جداً وممتازة 💪🟢");
                }
            });
        }
    </script>
</body>
</html>

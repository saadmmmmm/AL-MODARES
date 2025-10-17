<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة التعليم الإلكتروني - السادس العلمي</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --english: #e74c3c;
            --biology: #27ae60;
            --math: #f39c12;
            --light: #ecf0f1;
            --dark: #2c3e50;
        }

        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* الهيدر */
        .header {
            background: rgba(255, 255, 255, 0.95);
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            backdrop-filter: blur(10px);
        }

        .header h1 {
            color: var(--primary);
            font-size: 2.8em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .header p {
            color: #7f8c8d;
            font-size: 1.2em;
            margin-bottom: 20px;
        }

        .school-info {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 20px;
            flex-wrap: wrap;
        }

        .info-item {
            background: var(--light);
            padding: 15px 25px;
            border-radius: 50px;
            font-weight: bold;
            color: var(--dark);
        }

        /* المواد الدراسية */
        .subjects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .subject-card {
            background: white;
            border-radius: 20px;
            padding: 30px;
            text-align: center;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            border: 5px solid transparent;
            position: relative;
            overflow: hidden;
        }

        .subject-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
        }

        .subject-card.english {
            border-color: var(--english);
        }

        .subject-card.biology {
            border-color: var(--biology);
        }

        .subject-card.math {
            border-color: var(--math);
        }

        .subject-icon {
            font-size: 4em;
            margin-bottom: 20px;
            height: 100px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .english .subject-icon { color: var(--english); }
        .biology .subject-icon { color: var(--biology); }
        .math .subject-icon { color: var(--math); }

        .subject-card h2 {
            font-size: 2em;
            margin-bottom: 15px;
            color: var(--dark);
        }

        .subject-card p {
            color: #7f8c8d;
            margin-bottom: 25px;
            line-height: 1.6;
        }

        .btn {
            background: var(--secondary);
            color: white;
            padding: 12px 30px;
            border: none;
            border-radius: 50px;
            font-size: 1.1em;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-block;
            font-weight: bold;
        }

        .btn:hover {
            background: var(--primary);
            transform: scale(1.05);
        }

        /* المحاضرات */
        .lectures-section {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .section-title {
            text-align: center;
            color: var(--primary);
            font-size: 2.2em;
            margin-bottom: 30px;
            position: relative;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 100px;
            height: 4px;
            background: var(--secondary);
            margin: 10px auto;
            border-radius: 2px;
        }

        .lectures-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .lecture-card {
            background: var(--light);
            padding: 25px;
            border-radius: 15px;
            border-left: 5px solid var(--secondary);
            transition: transform 0.3s;
        }

        .lecture-card:hover {
            transform: translateX(10px);
        }

        .lecture-card h3 {
            color: var(--dark);
            margin-bottom: 10px;
            font-size: 1.3em;
        }

        .lecture-card p {
            color: #7f8c8d;
            margin-bottom: 15px;
        }

        .lecture-meta {
            display: flex;
            justify-content: space-between;
            color: var(--primary);
            font-size: 0.9em;
            margin-top: 15px;
        }

        /* الفوتر */
        .footer {
            background: var(--primary);
            color: rgb(250, 243, 243);
            text-align: center;
            padding: 30px;
            border-radius: 20px;
            margin-top: 40px;
        }

        .contact-info {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin: 20px 0;
            flex-wrap: wrap;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* القائمة الجانبية */
        .sidebar {
            position: fixed;
            left: 20px;
            top: 50%;
            transform: translateY(-50%);
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .quick-links {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .quick-link {
            background: var(--light);
            padding: 12px 20px;
            border-radius: 10px;
            text-decoration: none;
            color: var(--dark);
            text-align: center;
            transition: all 0.3s;
            font-weight: bold;
        }

        .quick-link:hover {
            background: var(--secondary);
            color: white;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .sidebar {
                display: none;
            }
            
            .header h1 {
                font-size: 2em;
            }
            
            .subjects-grid {
                grid-template-columns: 1fr;
            }
            
            .school-info {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- الهيدر -->
        <header class="header">
            <h1>🎓  منصة رويدة للتعليم</h1>
            <p>مرحباً بطلاب الصف السادس العلمي - الفصل الدراسي الأول  2026</p>
            <div class="school-info">
                <div class="info-item">📚 المرحلة: السادس العلمي</div>
                <div class="info-item">🎯 التخصص: علمي</div>
                <div class="info-item">📅 الفصل: الأول</div>
            </div>
        </header>

        <!-- القائمة الجانبية -->
        <nav class="sidebar">
            <div class="quick-links">
                <a href="#" class="quick-link">📖 الجدول الدراسي</a>
                <a href="#" class="quick-link">📝 الواجبات</a>
                <a href="#" class="quick-link">🎯 الاختبارات</a>
                <a href="#" class="quick-link">📊 النتائج</a>
                <a href="#" class="quick-link">👨‍🏫 المدرسون</a>
            </div>
        </nav>

        <!-- المواد الدراسية -->
        <section class="subjects-grid">
            <!-- مادة الإنجليزية -->
            <div class="subject-card english">
                <div class="subject-icon">
                    <i class="fas fa-language"></i>
                </div>
                <h2>اللغة الإنجليزية</h2>
                <p>تطوير مهارات القراءة، الكتابة، والمحادثة باللغة الإنجليزية مع تركيز على القواعد والمفردات الأكاديمية</p>
                <a href="#english-lectures" class="btn">عرض المحاضرات</a>
            </div>

            <!-- مادة الأحياء -->
            <div class="subject-card biology">
                <div class="subject-icon">
                    <i class="fas fa-dna"></i>
                </div>
                <h2>علم الأحياء</h2>
                <p>دراسة الكائنات الحية، الخلايا، الوراثة، والتطور مع تجارب عملية لفهم عالم الأحياء</p>
                <a href="#biology-lectures" class="btn">عرض المحاضرات</a>
            </div>

            <!-- مادة الرياضيات -->
            <div class="subject-card math">
                <div class="subject-icon">
                    <i class="fas fa-calculator"></i>
                </div>
                <h2>الرياضيات</h2>
                <p>تطوير المهارات الرياضية في الجبر، الهندسة، التفاضل والتكامل وحل المسائل المعقدة</p>
                <a href="#math-lectures" class="btn">عرض المحاضرات</a>
            </div>
        </section>

        <!-- محاضرات الإنجليزية -->
        <section id="english-lectures" class="lectures-section">
            <h2 class="section-title">محاضرات اللغة الإنجليزية</h2>
            <div class="lectures-grid">
                <div class="lecture-card">
                    <h3>المحاضرة 1: القواعد الأساسية</h3>
                    <p>شرح الأزمنة الأساسية في اللغة الإنجليزية والمفردات اليومية</p>
                    <div class="lecture-meta">
                        <span>⏱️ 45 دقيقة</span>
                        <span>📁 ورقة عمل</span>
                    </div>
                </div>
                <div class="lecture-card">
                    <h3>المحاضرة 2: القراءة المتقدمة</h3>
                    <p>تحليل النصوص الأدبية وتطوير مهارات الفهم القرائي</p>
                    <div class="lecture-meta">
                        <span>⏱️ 60 دقيقة</span>
                        <span>🎥 فيديو</span>
                    </div>
                </div>
                <div class="lecture-card">
                    <h3>المحاضرة 3: الكتابة الأكاديمية</h3>
                    <p>تعلم كتابة المقالات والتقارير باللغة الإنجليزية</p>
                    <div class="lecture-meta">
                        <span>⏱️ 50 دقيقة</span>
                        <span>📝 تمرين</span>
                    </div>
                </div>
            </div>
        </section>

        <!-- محاضرات الأحياء -->
        <section id="biology-lectures" class="lectures-section">
            <h2 class="section-title">محاضرات علم الأحياء</h2>
            <div class="lectures-grid">
                <div class="lecture-card">
                    <h3>المحاضرة 1: الخلية الحية</h3>
                    <p>دراسة مكونات الخلية والعمليات الحيوية الأساسية</p>
                    <div class="lecture-meta">
                        <span>⏱️ 55 دقيقة</span>
                        <span>🔬 تجربة</span>
                    </div>
                </div>
                <div class="lecture-card">
                    <h3>المحاضرة 2: الوراثة والجينات</h3>
                    <p>فهم قوانين مندل وتطبيقاتها في الوراثة البشرية</p>
                    <div class="lecture-meta">
                        <span>⏱️ 65 دقيقة</span>
                        <span>📊 رسم بياني</span>
                    </div>
                </div>
                <div class="lecture-card">
                    <h3>المحاضرة 3: التطور والنشوء</h3>
                    <p>نظريات التطور والانتخاب الطبيعي وتطبيقاتها</p>
                    <div class="lecture-meta">
                        <span>⏱️ 70 دقيقة</span>
                        <span>📖 بحث</span>
                    </div>
                </div>
            </div>
        </section>

        <!-- محاضرات الرياضيات -->
        <section id="math-lectures" class="lectures-section">
            <h2 class="section-title">محاضرات الرياضيات</h2>
            <div class="lectures-grid">
                <div class="lecture-card">
                    <h3>المحاضرة 1: الدوال والرسوم البيانية</h3>
                    <p>تحليل الدوال الرياضية وتمثيلها بيانياً</p>
                    <div class="lecture-meta">
                        <span>⏱️ 50 دقيقة</span>
                        <span>📈 رسم بياني</span>
                    </div>
                </div>
                <div class="lecture-card">
                    <h3>المحاضرة 2: التفاضل والتكامل</h3>
                    <p>مقدمة في حساب التفاضل والتكامل وتطبيقاته</p>
                    <div class="lecture-meta">
                        <span>⏱️ 75 دقيقة</span>
                        <span>📝 مسائل</span>
                    </div>
                </div>
                <div class="lecture-card">
                    <h3>المحاضرة 3: الهندسة التحليلية</h3>
                    <p>دراسة الأشكال الهندسية باستخدام الإحداثيات</p>
                    <div class="lecture-meta">
                        <span>⏱️ 60 دقيقة</span>
                        <span>📐 أشكال</span>
                    </div>
                </div>
            </div>
        </section>

        <!-- الفوتر -->
        <footer class="footer">
            <h3>منصة التعليم الإلكتروني - السادس العلمي</h3>
            <div class="contact-info">
                <div class="contact-item">
                    <i class="fas fa-envelope"></i>
                    <span>contact@school.edu.iq</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <span>+964 770 123 4567</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <span>بابل - العراق</span>
                </div>
            </div>
            <p>© 2026 جميع الحقوق محفوظة - منصة التعليم الإلكتروني</p>
        </footer>
    </div>

    <script>
        // كود الجافاسكريبت للتفاعل
        document.addEventListener('DOMContentLoaded', function() {
            // تأثير سلس للتمرير
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    const target = document.querySelector(this.getAttribute('href'));
                    if (target) {
                        target.scrollIntoView({
                            behavior: 'smooth',
                            block: 'start'
                        });
                    }
                });
            });

            // إضافة تأثير للبطاقات عند التمرير
            const observerOptions = {
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            };

            const observer = new IntersectionObserver(function(entries) {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, observerOptions);

            // تطبيق التأثير على عناصر الموقع
            document.querySelectorAll('.subject-card, .lecture-card').forEach(card => {
                card.style.opacity = '0';
                card.style.transform = 'translateY(20px)';
                card.style.transition = 'opacity 0.6s, transform 0.6s';
                observer.observe(card);
            });
        });
    </script>
</body>
</html>

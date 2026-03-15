<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>পাবলিক প্রকিউরমেন্ট স্কিল অ্যাসেসমেন্ট</title>
    <style>
        /* Uniform Font applied to all elements */
        * { font-family: 'Kalpurush', Arial, sans-serif; box-sizing: border-box; }
        body { background-color: #f4f6f9; color: #2c3e50; margin: 0; padding: 20px; }
        .container { max-width: 1050px; margin: 0 auto; background: #ffffff; padding: 35px; border-radius: 12px; box-shadow: 0 10px 25px rgba(0,0,0,0.08); }
        h1 { text-align: center; color: #2980b9; border-bottom: 2px solid #3498db; padding-bottom: 15px; margin-bottom: 10px; }
        h2.section-title { color: #2c3e50; border-left: 5px solid #1abc9c; padding-left: 10px; margin-top: 40px; margin-bottom: 25px; background: #fdfefe; padding-top: 5px; padding-bottom: 5px; }
        
        .module-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 20px; margin-bottom: 30px; }
        .module-card { background: #fdfefe; border: 1px solid #e0e0e0; border-radius: 8px; padding: 20px; box-shadow: 0 4px 6px rgba(0,0,0,0.05); transition: transform 0.2s; }
        .module-card:hover { transform: translateY(-5px); border-color: #3498db; box-shadow: 0 8px 15px rgba(0,0,0,0.1); }
        .module-card h3 { margin-top: 0; color: #2c3e50; font-size: 19px; border-bottom: 2px dashed #ecf0f1; padding-bottom: 10px; margin-bottom: 15px; }
        .lesson-btn { display: block; width: 100%; background: #ebf5fb; color: #2980b9; border: 1px solid #d6eaf8; padding: 12px 10px; margin-bottom: 10px; border-radius: 5px; cursor: pointer; font-weight: bold; font-size: 16px; text-align: left; transition: background 0.2s; }
        .lesson-btn:hover { background: #d6eaf8; color: #154360; }
        .lesson-btn span { float: right; }

        .modal { display: none; position: fixed; z-index: 1000; left: 0; top: 0; width: 100%; height: 100%; background-color: rgba(0,0,0,0.6); backdrop-filter: blur(4px); }
        .modal-content { background-color: #fefefe; margin: 3% auto; padding: 40px; border-radius: 12px; width: 90%; max-width: 850px; max-height: 90vh; overflow-y: auto; box-shadow: 0 15px 30px rgba(0,0,0,0.2); position: relative; }
        .close-btn { color: #e74c3c; position: absolute; top: 20px; right: 25px; font-size: 35px; font-weight: bold; cursor: pointer; line-height: 20px; }
        .close-btn:hover { color: #c0392b; }
        
        .modal-body { font-size: 18px; line-height: 1.7; color: #34495e; }
        .modal-body h2 { color: #2980b9; margin-top: 0; border-bottom: 2px solid #ecf0f1; padding-bottom: 10px; font-size: 26px; text-align: center;}
        .modal-body h3 { color: #16a085; margin-top: 35px; margin-bottom: 15px; font-size: 22px; border-left: 5px solid #16a085; padding-left: 12px; background: #e8f8f5; padding-top: 8px; padding-bottom: 8px; border-radius: 4px;}
        
        .definition-text { color: #2c3e50; margin-bottom: 10px;}
        .explanation-text { color: #566573; margin-bottom: 15px;}
        .badge-def { background-color: #3498db; color: white; padding: 3px 8px; border-radius: 4px; font-size: 15px; margin-right: 5px;}
        .badge-exp { background-color: #9b59b6; color: white; padding: 3px 8px; border-radius: 4px; font-size: 15px; margin-right: 5px;}

        .example-box { background: #fff8e1; border-left: 6px solid #f39c12; padding: 15px 20px; margin-top: 15px; margin-bottom: 25px; border-radius: 0 5px 5px 0; font-size: 17px; }
        .example-box strong { color: #d35400; font-size: 18px; display: block; margin-bottom: 5px;}
        
        .info-box { background: #e8f6f3; padding: 20px; border-left: 6px solid #1abc9c; margin-bottom: 25px; font-size: 17px; border-radius: 4px; line-height: 1.6; }
        
        .btn { display: inline-block; width: 100%; padding: 16px; background-color: #3498db; color: white; border: none; border-radius: 8px; font-size: 20px; font-weight: bold; cursor: pointer; transition: all 0.3s ease; text-align: center; }
        .btn:hover { background-color: #21618c; transform: translateY(-2px); }
        .btn:disabled { background-color: #bdc3c7; cursor: not-allowed; transform: none; }
        .btn-submit { background-color: #27ae60; }
        .btn-submit:hover { background-color: #1e8449; }
        .hint-btn { background-color: #f39c12; width: auto; padding: 16px 25px; }
        .hint-btn:hover { background-color: #d68910; }
        .hint-btn:disabled { background-color: #f8c471; cursor: not-allowed; transform: none; opacity: 0.7;}
        
        #header-bar { display: flex; justify-content: space-between; align-items: center; background: #ecf0f1; padding: 15px 20px; border-radius: 8px; margin-bottom: 25px; font-weight: bold; font-size: 18px; }
        .timer { color: #c0392b; font-size: 22px; display: flex; align-items: center; gap: 8px;}
        .question-box { margin-bottom: 30px; min-height: 250px; }
        .question-text { font-size: 20px; font-weight: bold; margin-bottom: 20px; line-height: 1.5; color: #34495e; }
        .q-type-badge { display: inline-block; background: #f39c12; color: white; padding: 4px 10px; border-radius: 4px; font-size: 14px; margin-bottom: 10px; }
        
        .options label { display: block; background: #fdfefe; padding: 16px; margin-bottom: 12px; border: 2px solid #e0e0e0; border-radius: 8px; cursor: pointer; font-size: 18px; transition: all 0.2s; }
        .options label:hover { background: #ebf5fb; border-color: #3498db; }
        input[type="radio"] { margin-right: 15px; transform: scale(1.3); accent-color: #3498db; cursor: pointer; }
        
        .fib-input { font-size: 18px; padding: 8px 12px; border: 2px solid #3498db; border-radius: 6px; margin: 0 10px; width: 200px; color: #c0392b; font-weight: bold; text-align: center; }
        .fib-hints-box { margin-top: 20px; padding: 15px; background: #e8f8f5; border-left: 4px solid #1abc9c; border-radius: 5px; font-size: 18px; }
        .fib-hint-badge { display: inline-block; background: #1abc9c; color: white; padding: 6px 15px; margin: 5px 8px; border-radius: 20px; cursor: pointer; font-weight: bold; transition: background 0.3s; box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
        .fib-hint-badge:hover { background: #16a085; }

        .order-step-container { background: #f9f9f9; padding: 15px; margin-bottom: 10px; border-left: 4px solid #8e44ad; border-radius: 5px; display: flex; align-items: center; }
        .order-step-label { font-weight: bold; margin-right: 15px; width: 80px; }
        .order-select { flex-grow: 1; padding: 10px; font-size: 16px; border: 1px solid #ccc; border-radius: 5px; cursor: pointer; }

        .navigation-btns { display: flex; justify-content: space-between; gap: 15px; }
        .nav-right { display: flex; gap: 15px; flex-grow: 1; justify-content: flex-end;}
        
        .result-item { margin-bottom: 20px; padding: 20px; border-radius: 8px; border: 1px solid #ddd; line-height: 1.6; font-size: 17px; }
        .correct-ans { background-color: #eafaf1; border-left: 5px solid #2ecc71; }
        .wrong-ans { background-color: #fdedec; border-left: 5px solid #e74c3c; }
        .unanswered { background-color: #fef9e7; border-left: 5px solid #f1c40f; }
        
        .developer-credit { text-align: center; margin-top: 40px; font-size: 17px; color: #7f8c8d; font-weight: bold; border-top: 1px solid #eee; padding-top: 20px;}
        .hidden { display: none !important; }
    </style>
</head>
<body>

<div class="container">
    <div id="start-screen">
        <h1>পাবলিক প্রকিউরমেন্ট ই-লার্নিং ও স্কিল অ্যাসেসমেন্ট</h1>
        
        <h2 class="section-title">📚 লার্নিং জোন (PPR স্টাডি মডিউল)</h2>
        <p style="color: #7f8c8d; font-size: 17px; margin-bottom: 20px;">পরীক্ষা দেওয়ার পূর্বে নিচের ১৩টি মডিউল পড়ে আপনার প্রকিউরমেন্ট জ্ঞান ঝালিয়ে নিন। প্রতিটি কনসেপ্ট সহজ সংজ্ঞা, ব্যাখ্যা ও বাস্তব উদাহরণসহ সাজানো হয়েছে।</p>
        
        <div class="module-grid" id="module-container"></div>

        <h2 class="section-title">✍️ টেস্ট জোন</h2>
        <div class="info-box">
            <p><strong>পরীক্ষার নিয়মাবলি ও নির্দেশিকা:</strong></p>
            <ul>
                <li>সিস্টেমের <strong>বিশাল প্রশ্নব্যাংক (১৫০+ প্রশ্ন)</strong> থেকে স্বয়ংক্রিয়ভাবে বাছাইকৃত <strong>৬০টি প্রশ্ন</strong> আপনাকে দেওয়া হবে। প্রতিবার টেস্টে নতুন প্রশ্ন আসবে।</li>
                <li>পরীক্ষা শুরুর পর আপনি <strong>পূর্ববর্তী প্রশ্নে ফিরে যেতে পারবেন না</strong>।</li>
                <li style="color: #c0392b;"><strong>সতর্কতা ১ (Tab Switch):</strong> পরীক্ষা চলাকালে <strong>অন্য কোনো ট্যাবে গেলে বা ব্রাউজার মিনিমাইজ করলে</strong> টেস্ট সাথে সাথে বাতিল হয়ে যাবে।</li>
                <li style="color: #c0392b;"><strong>সতর্কতা ২ (Time Limit):</strong> কোনো একক প্রশ্নে <strong>৩ মিনিটের বেশি</strong> সময় নিলে টাইম-আউট হয়ে যাবে।</li>
                <li><strong>💡 হিন্টস অপশন:</strong> হিন্টস নিলে MCQ তে ১টি ভুল অপশন কমবে, FIB তে সম্ভাব্য উত্তর দেখাবে এবং ফ্লোচার্টে ১ম ধাপটি সঠিক করে দেওয়া হবে।</li>
                <li>মোট সময়কাল: <strong>১ ঘণ্টা (৬০ মিনিট)</strong>। নেগেটিভ মার্কিং নেই।</li>
            </ul>
        </div>
        <button class="btn" onclick="startTest()">টেস্ট শুরু করুন</button>
        
        <div class="developer-credit">ডেভেলপার- মনির হোসেন</div>
    </div>

    <div id="quiz-screen" class="hidden">
        <div id="header-bar">
            <div>প্রশ্ন: <span id="current-q-num">1</span>/<span id="total-q-count">60</span></div>
            <div style="text-align: center; color: #e67e22; font-size: 15px;">বর্তমান প্রশ্নের সময়<br><span id="q-time-left" style="font-size: 20px; font-weight: bold;">03:00</span></div>
            <div class="timer">মোট সময় ⏳ <span id="time-left">60:00</span></div>
        </div>
        
        <div class="question-box">
            <span class="q-type-badge" id="q-type-badge">MCQ</span>
            <div class="question-text" id="question-text">Loading...</div>
            <div id="answer-container"></div>
        </div>

        <div class="navigation-btns">
            <button class="btn hint-btn" id="hint-btn" onclick="useHint()">💡 হিন্টস নিন</button>
            <div class="nav-right">
                <button class="btn" id="next-btn" onclick="nextQuestion()">পরবর্তী প্রশ্ন ➡️</button>
                <button class="btn btn-submit hidden" id="submit-btn" onclick="submitTest()">টেস্ট জমা দিন ✅</button>
            </div>
        </div>
    </div>

    <div id="result-screen" class="hidden">
        <h1>আপনার টেস্টের ফলাফল</h1>
        <h2 id="score-display" style="font-size:32px; color:#2980b9; text-align: center;">স্কোর: 0/60</h2>
        <button class="btn" style="margin-bottom:30px;" onclick="location.reload()">পুনরায় টেস্ট দিন</button>
        <div id="review-container"></div>
        <div class="developer-credit">ডেভেলপার- মনির হোসেন</div>
    </div>
</div>

<div id="lesson-modal" class="modal">
    <div class="modal-content">
        <span class="close-btn" onclick="closeModal()">&times;</span>
        <div class="modal-body" id="modal-body"></div>
    </div>
</div>

<script>
    // ================= LEARNING MODULES DATA =================
    const learningModules = [
        {
            title: "মডিউল ১: সাধারণ বিধান ও সংজ্ঞা (অধ্যায় ১)",
            lessons: [
                {
                    title: "১.১ বেসিক ধারণা ও প্রতিষ্ঠানসমূহ",
                    content: `<h2>বেসিক ধারণা ও প্রতিষ্ঠানসমূহ</h2>
                    
                    <h3>১. পাবলিক প্রকিউরমেন্ট (Public Procurement)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> সরকারি বা জনগণের তহবিলের অর্থে জনগণের সেবার উদ্দেশ্যে কোনো পণ্য (Goods), পূর্ত কাজ (Works) বা সেবা (Services) ক্রয় করার সামগ্রিক প্রক্রিয়া।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> সরকার যখন ট্যাক্সের টাকা দিয়ে দেশের উন্নয়নের জন্য কিছু কেনে বা বানায়, তখন নির্দিষ্ট স্বচ্ছ নিয়ম মেনে তা করতে হয়। এই নিয়ম মেনে কেনাকাটাই হলো পাবলিক প্রকিউরমেন্ট।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> স্বাস্থ্য মন্ত্রণালয় জনগণের চিকিৎসার জন্য সরকারি টাকায় ১০০টি অ্যাম্বুলেন্স কিনছে। এটি একটি পাবলিক প্রকিউরমেন্ট।</div>

                    <h3>২. ক্রয়কারী সংস্থা (Procuring Entity – PE)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> যে সরকারি দপ্তর বা সংস্থা সরকারি অর্থে ক্রয় কার্য সম্পাদন করে তাকে ক্রয়কারী সংস্থা বলে।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> মন্ত্রণালয় বা দপ্তরের যে ইউনিটটি সরাসরি টেন্ডার আহ্বান করে এবং চুক্তিতে স্বাক্ষর করে।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> একটি নতুন সেতু নির্মাণের জন্য "স্থানীয় সরকার প্রকৌশল অধিদপ্তর (LGED)" টেন্ডার ডাকল। এখানে LGED হলো ক্রয়কারী সংস্থা (PE)।</div>

                    <h3>৩. HOPE (Head of Procuring Entity)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> ক্রয়কারী সংস্থার প্রধান কর্মকর্তা, যার নামে টেন্ডার হয় এবং যিনি চূড়ান্ত অনুমোদন দেন।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> একটি দপ্তরের সর্বোচ্চ ক্ষমতাপ্রাপ্ত ব্যক্তি যিনি যেকোনো ক্রয় চুক্তির চূড়ান্ত দায়ভার বহন করেন।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> LGED এর ক্ষেত্রে 'প্রধান প্রকৌশলী' (Chief Engineer) হলেন HOPE।</div>`
                },
                {
                    title: "১.২ গুরুত্বপূর্ণ পরিভাষা",
                    content: `<h2>গুরুত্বপূর্ণ পরিভাষা</h2>
                    
                    <h3>১. ইকোনমিক অপারেটর (Economic Operator)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> সরকারি দরপত্রে অংশগ্রহণকারী সরবরাহকারী, ঠিকাদার, সেবাদানকারী ও পরামর্শকদের সমষ্টিগত নাম।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> যারা সরকারের কাছে জিনিস বিক্রি করে বা কাজ করে দেয়, আধুনিক প্রকিউরমেন্টে তাদের সবাইকে এক নামে ইকোনমিক অপারেটর বলা হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> রফিক সাহেবের একটি কনস্ট্রাকশন কোম্পানি আছে এবং তিনি টেন্ডারে অংশ নিয়েছেন। রফিক সাহেব এখানে একজন ইকোনমিক অপারেটর।</div>

                    <h3>২. বৈধতা মেয়াদ (Bid Validity Period)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> দরপত্র দাখিলের পর থেকে যত দিন পর্যন্ত দরদাতার প্রস্তাবিত দাম ও শর্ত অপরিবর্তিত ও কার্যকর থাকে।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> ঠিকাদার যে দামে কাজ করতে রাজি হয়েছে, সেই দামটি একটি নির্দিষ্ট সময় (সাধারণত ৬০-১৫০ দিন) পর্যন্ত লক থাকে। এই সময়ের মধ্যে ক্রয়কারীকে মূল্যায়ন শেষ করে চুক্তি করতে হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> একটি টেন্ডারের বৈধতা ৬০ দিন। ঠিকাদার ১ লাখ টাকায় কম্পিউটার দিতে চেয়েছে। ৬০ দিনের মধ্যে কম্পিউটারের দাম বাজারে বেড়ে গেলেও ঠিকাদার ১ লাখ টাকাতেই তা দিতে বাধ্য থাকবে।</div>`
                }
            ]
        },
        {
            title: "মডিউল ২: ক্রয় পরিকল্পনা (অধ্যায় ২)",
            lessons: [
                {
                    title: "২.১ বার্ষিক ক্রয় পরিকল্পনা (APP)",
                    content: `<h2>বার্ষিক ক্রয় পরিকল্পনা (APP)</h2>
                    
                    <h3>বার্ষিক ক্রয় পরিকল্পনা (Annual Procurement Plan)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> একটি অর্থবছরে কোনো সরকারি দপ্তর কী কী কিনবে, কত টাকার কিনবে এবং কবে কিনবে তার আগাম পূর্ণাঙ্গ পরিকল্পনা।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> পিপিআর অনুযায়ী, অর্থবছর শুরুর আগেই এই পরিকল্পনা তৈরি ও অনুমোদন করতে হয়। APP ছাড়া e-GP সিস্টেমে কোনো টেন্ডার ডাকা যায় আসাম।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> একটি বিশ্ববিদ্যালয় বছরের শুরুতেই প্ল্যান করে রাখল যে এই বছর তারা ১ কোটি টাকায় ল্যাব সরঞ্জাম কিনবে, জুলাই মাসে টেন্ডার ডাকবে এবং অক্টোবরে কাজ শেষ করবে। এটিই তাদের APP।</div>`
                },
                {
                    title: "২.২ ক্রয় কৌশল উন্নয়ন (Strategy)",
                    content: `<h2>ক্রয় কৌশল উন্নয়ন</h2>
                    
                    <h3>ক্রয় কৌশল (Procurement Strategy)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> প্রকল্পের আকার, বাজার পরিস্থিতি ও ঝুঁকি বিশ্লেষণ করে সবচেয়ে উপযুক্ত ক্রয় পদ্ধতি ও সময়সীমা নির্ধারণ করার পরিকল্পনা।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> পিপিআর-২০২৫ অনুযায়ী, বড় বা জটিল ক্রয়ের ক্ষেত্রে APP এর পাশাপাশি একটি দীর্ঘমেয়াদি কৌশল তৈরি করা বাধ্যতামূলক, যাতে ঝুঁকি এড়ানো যায়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> সরকার একটি আধুনিক ডেটা সেন্টার বানাবে। যেহেতু সাধারণ ঠিকাদাররা এটি পারবে না, তাই কৌশলে নির্ধারণ করা হলো যে 'দ্বি-ধাপ দরপত্র (Two-stage)' পদ্ধতি ব্যবহার করা হবে।</div>`
                }
            ]
        },
        {
            title: "মডিউল ৩: ক্রয় পদ্ধতি (অধ্যায় ৩)",
            lessons: [
                {
                    title: "৩.১ OTM, LTM ও DPM",
                    content: `<h2>প্রধান ক্রয় পদ্ধতিসমূহ</h2>
                    
                    <h3>১. উন্মুক্ত দরপত্র পদ্ধতি (OTM - Open Tendering Method)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> যে পদ্ধতিতে টেন্ডার উন্মুক্ত বিজ্ঞপ্তির মাধ্যমে ডাকা হয় এবং যোগ্য যে কেউ এতে অংশ নিতে পারে।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> এটি সরকারি ক্রয়ের ডিফল্ট বা প্রধান পদ্ধতি। এটি সবচেয়ে বেশি প্রতিযোগিতামূলক।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> পুলিশ সদর দপ্তর ৫০টি জিপ গাড়ি কিনবে। তারা e-GP তে OTM টেন্ডার দিল। যেকোনো গাড়ির ডিলার এতে অংশ নিতে পারবে।</div>

                    <h3>২. সীমিত দরপত্র পদ্ধতি (LTM - Limited Tendering Method)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> যে পদ্ধতিতে কেবল পূর্ব থেকে তালিকাভুক্ত বা নির্দিষ্ট কিছু ঠিকাদারকে দরপত্রে অংশ নেওয়ার আমন্ত্রণ জানানো হয়।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> যখন নির্দিষ্ট কোনো পণ্য খুব কম সংখ্যক সরবরাহকারীর কাছে থাকে অথবা ছোট পূর্তকাজের ক্ষেত্রে (পিপিআর-২০২৫ অনুযায়ী ৫ কোটি টাকা পর্যন্ত) এটি ব্যবহৃত হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> একটি স্কুলের বাউন্ডারি ওয়াল নির্মাণ (খরচ ৩ কোটি টাকা)। এখানে শুধু ওই জেলার তালিকাভুক্ত ঠিকাদাররা টেন্ডার দিল এবং লটারির মাধ্যমে একজনকে বিজয়ী করা হলো।</div>

                    <h3>৩. সরাসরি ক্রয় পদ্ধতি (DPM - Direct Procurement Method)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> কোনো প্রতিযোগিতা ছাড়া সরাসরি একক সরবরাহকারীর সাথে চুক্তি করার পদ্ধতি।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> অত্যন্ত জরুরি প্রয়োজন, দুর্যোগ মোকাবিলা বা পেটেন্টকৃত পণ্যের ক্ষেত্রে এটি ব্যবহৃত হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> করোনা মহামারির চরম মুহূর্তে একদিনও দেরি করার সুযোগ নেই। সরকার DPM পদ্ধতিতে সরাসরি একটি বড় কোম্পানির সাথে চুক্তি করে ৫ লক্ষ পিপিই কিনে নিল।</div>`
                },
                {
                    title: "৩.২ দরপত্রের প্রকারভেদ (OSTETM, Two-Stage)",
                    content: `<h2>দরপত্রের প্রকারভেদ</h2>
                    
                    <h3>১. এক ধাপ দুই খাম (OSTETM - One Stage Two Envelope)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> যেখানে কারিগরি (Technical) এবং আর্থিক (Financial) প্রস্তাব একই সময়ে দুটি আলাদা খামে বা ফোল্ডারে জমা দেওয়া হয়।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> জটিল কারিগরি কাজের ক্ষেত্রে এটি ব্যবহৃত হয়। প্রথমে শুধু Technical খাম খুলে অভিজ্ঞতা যাচাই করা হয়। যারা পাস করে, শুধু তাদেরই Financial খাম খুলে সবচেয়ে কম দরদাতাকে কাজ দেওয়া হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> আধুনিক হাসপাতাল নির্মাণের টেন্ডার। যে ঠিকাদারের হাসপাতাল বানানোর পূর্ব অভিজ্ঞতা নেই, তার কারিগরি খাম বাতিল হয়ে যাবে এবং তার আর্থিক খাম (দামের খাম) না খুলেই ফেরত দেওয়া হবে।</div>

                    <h3>২. দ্বি-ধাপ দরপত্র (Two-stage Tendering)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> যেখানে প্রথমে কারিগরি প্রস্তাবনা (ধারণা) চাওয়া হয়, আলোচনা শেষে চূড়ান্ত ডিজাইনের ওপর দ্বিতীয় ধাপে দরপত্র চাওয়া হয়।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> যখন ক্রয়কারী ঠিকভাবে কারিগরি স্পেসিফিকেশন বুঝতে পারে না, তখন এটি ব্যবহার হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> একটি স্মার্ট সিটি সফটওয়্যার বানানো হবে। প্রথমে আইটি ফার্মগুলো তাদের কনসেপ্ট জমা দিল। সরকার সবচেয়ে ভালো কনসেপ্টটি চূড়ান্ত করে দ্বিতীয় ধাপে শুধু ফাইন্যান্সিয়াল দরপত্র ডাকল।</div>`
                }
            ]
        },
        {
            title: "মডিউল ৪: পণ্য ক্রয় (অধ্যায় ৪)",
            lessons: [
                {
                    title: "৪.১ পণ্য ক্রয় (RFQ) ও স্পেসিফিকেশন",
                    content: `<h2>পণ্য ক্রয় (Goods)</h2>
                    
                    <h3>১. কোটেশন পদ্ধতি (RFQ - Request for Quotation)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> জরুরি ও স্বল্পমূল্যের সাধারণ পণ্য কেনার জন্য কমপক্ষে ৩ জন সরবরাহকারীর কাছ থেকে দরপত্র (কোটেশন) নেওয়ার পদ্ধতি।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> এটি সর্বোচ্চ ৫ লক্ষ টাকা পর্যন্ত ক্রয়ের ক্ষেত্রে ব্যবহার করা যায়। এতে লম্বা টেন্ডার প্রক্রিয়ার প্রয়োজন হয় না।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> অফিসে হঠাৎ এসি নষ্ট। গরমে কাজ করা যাচ্ছে না। অফিস প্রধান ৩টি এসির দোকান থেকে কোটেশন এনে যে কম দাম দিয়েছে তার কাছ থেকে ১ লাখ টাকায় দ্রুত এসি কিনে ফেললেন।</div>

                    <h3>২. কারিগরি বিনির্দেশ (Technical Specification)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> পণ্যের মান, বৈশিষ্ট্য, কর্মক্ষমতা এবং উপাদানের সুনির্দিষ্ট ও পরিমাপযোগ্য বর্ণনা।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> দরপত্রে স্পেসিফিকেশন এমনভাবে লিখতে হয় যাতে কোনো নির্দিষ্ট ব্র্যান্ডকে পক্ষপাতিত্ব করা না হয় (যেমন 'সনি ব্র্যান্ডের টিভি' বলা যাবে না)।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> ল্যাপটপ কেনার দরপত্রে লেখা হলো: প্রসেসর কোর আই-৭, র‍্যাম ১৬ জিবি, স্টোরেজ ৫১২ জিবি এসএসডি। এটি হলো স্পেসিফিকেশন।</div>`
                }
            ]
        },
        {
            title: "মডিউল ৫: পূর্ত কাজ ক্রয় (অধ্যায় ৫)",
            lessons: [
                {
                    title: "৫.১ পূর্ত কাজ ও বিশেষ পদ্ধতি",
                    content: `<h2>পূর্ত কাজ (Works) ও বিশেষ চুক্তি</h2>
                    
                    <h3>১. ফোর্স অ্যাকাউন্ট (Force Account)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> সরকারি দপ্তর যখন ঠিকাদার নিয়োগ না করে নিজস্ব জনবল ও সরঞ্জাম ব্যবহার করে ছোটখাটো কাজ নিজেরাই সম্পন্ন করে।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> একক কার্যের সর্বোচ্চ মূল্যসীমা ৩ লক্ষ টাকা।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> পৌরসভার নিজস্ব বুলডোজার ও লেবার আছে। তারা রাস্তার একটি ভাঙা অংশ আড়াই লাখ টাকায় নিজেরাই মেরামত করে ফেলল।</div>

                    <h3>২. নকশা ও নির্মাণ (Design and Build - D&B)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> যে চুক্তিতে ঠিকাদার প্রতিষ্ঠান নিজেই প্রজেক্টের স্ট্রাকচারাল ডিজাইন করে এবং নিজেই তা নির্মাণ করে।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> সাধারণ টেন্ডারে সরকার ডিজাইন দেয়, ঠিকাদার বানায়। কিন্তু D&B তে ঠিকাদার উভয় দায়িত্ব পালন করে।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> পদ্মা সেতু প্রকল্পে ঠিকাদার কোম্পানিকে বলা হলো নদী শাসনের ডিজাইনও তোমরা করবে এবং বাস্তবায়নও তোমরা করবে।</div>

                    <h3>৩. টার্ন-কি চুক্তি (Turn-key Contract)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> নকশা-নির্মাণ-সরঞ্জাম ক্রয় ও স্থাপন করে সম্পূর্ণ চালু অবস্থায় (Ready to use) হস্তান্তর করার চুক্তি।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> চাবি ঘুরোলেই কাজ শুরু হবে—এমন অবস্থায় প্রজেক্ট বুঝিয়ে দেওয়া হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> সরকার একটি বিদ্যুৎকেন্দ্র নির্মাণের জন্য টার্ন-কি চুক্তি করল। ঠিকাদার মাটি কাটা থেকে শুরু করে জেনারেটর বসানো সব কাজ শেষ করে, বিদ্যুৎ উৎপাদন চালু করে চাবি সরকারের হাতে বুঝিয়ে দেবে।</div>`
                }
            ]
        },
        {
            title: "মডিউল ৬: সেবা ক্রয় (অধ্যায় ৬)",
            lessons: [
                {
                    title: "৬.১ পরামর্শক সেবা ও নির্বাচন পদ্ধতি",
                    content: `<h2>পরামর্শক সেবা (Consulting)</h2>
                    
                    <h3>১. QCBS (Quality and Cost Based Selection)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> কাজের মান (Quality/Technical) এবং অর্থ (Cost/Financial)- দুইয়ের ওপর ভিত্তি করে কম্বাইন্ড স্কোর করে পরামর্শক নির্বাচনের পদ্ধতি।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> এখানে গুণগত মানকে বেশি গুরুত্ব দেওয়া হয় (যেমন: মান ৮০%, মূল্য ২০%)।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> একটি জটিল সেতু ডিজাইনের জন্য আর্কিটেক্ট খোঁজা হচ্ছে। যার অভিজ্ঞতা (কোয়ালিটি) বেশি, তার দাম একটু বেশি হলেও সে-ই কাজ পাবে।</div>

                    <h3>২. LCS (Least Cost Selection)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> রুটিন বা সাধারণ পরামর্শক সেবার জন্য প্রযুক্তিগতভাবে পাস করা দরদাতাদের মধ্যে সর্বনিম্ন দরদাতাকে কাজ দেওয়ার পদ্ধতি।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> যেখানে কাজের মান নির্দিষ্ট (যেমন অডিট), সেখানে যে সবচেয়ে কম টাকা চাইবে সে কাজ পাবে।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> একটি দপ্তরের অ্যাকাউন্টস অডিট করতে হবে। যারা অডিট করার যোগ্য, তাদের মধ্যে যে ফার্ম সবচেয়ে কম ফিতে অডিট করতে রাজি হবে, তাকেই কাজ দেওয়া হবে।</div>`
                },
                {
                    title: "৬.২ ভৌত সেবা, ফ্রেমওয়ার্ক ও স্বার্থের সংঘাত",
                    content: `<h2>ভৌত সেবা ও অন্যান্য ধারণা</h2>

                    <h3>১. ভৌত সেবা (Physical Services)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> আউটসোর্সিংয়ের মাধ্যমে শ্রম বা কায়িক পরিশ্রমভিত্তিক সেবা গ্রহণ করা।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> সরকারি হাসপাতালে পরিচ্ছন্নতা বজায় রাখার জন্য একটি ক্লিনিং কোম্পানির সাথে টেন্ডার করে প্রতিদিন ২০ জন পরিচ্ছন্নতাকর্মী নিয়োগ দেওয়া।</div>

                    <h3>২. ফ্রেমওয়ার্ক চুক্তি (Framework Agreement)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> বারবার প্রয়োজনীয় পণ্য বা সেবার জন্য বারবার টেন্ডার না করে ১-৩ বছর মেয়াদি একটি সার্বিক চুক্তি করে রাখা।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> প্রয়োজন অনুযায়ী 'কল-অফ অর্ডার' ইস্যু করে পণ্য নেওয়া হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> একটি মন্ত্রণালয়ে সারা বছর কাগজ ও কলম লাগে। তারা একটি দোকানের সাথে ২ বছরের ফ্রেমওয়ার্ক চুক্তি করল। যখনই কাগজ শেষ হয়, শুধু একটা ফোন দেয়, দোকানদার কাগজ দিয়ে যায়।</div>

                    <h3>৩. স্বার্থের সংঘাত (Conflict of Interest)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> যখন কোনো ব্যক্তির ব্যক্তিগত বা ব্যবসায়িক স্বার্থ তার পেশাগত নিরপেক্ষতাকে নষ্ট করে।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> কোনো আর্কিটেক্ট ফার্ম যদি একটি ভবনের নকশা (Design) প্রণয়নের কাজ করে, তবে ওই ভবনের নির্মাণ কাজের তদারকি বা ঠিকাদারি কাজ তারা কোনোভাবেই পেতে পারেবিধা।</div>`
                }
            ]
        },
        {
            title: "মডিউল ৭: আন্তর্জাতিক ক্রয় (অধ্যায় ৭)",
            lessons: [
                {
                    title: "৭.১ আন্তর্জাতিক ক্রয় (ICT) ও এল/সি",
                    content: `<h2>আন্তর্জাতিক ক্রয় পদ্ধতি</h2>
                    
                    <h3>১. আন্তর্জাতিক উন্মুক্ত দরপত্র (ICT - International Competitive Tendering)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> দেশের বাজারে মেগা প্রজেক্ট বা জটিল পণ্য পাওয়ার সক্ষমতা না থাকলে সারা বিশ্বের জন্য গ্লোবাল টেন্ডার ডাকা হয়।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> ন্যূনতম সময়সীমা ৪২ দিন। দরপত্র সাধারণত বৈদেশিক মুদ্রায় হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> মেট্রোরেলের বগি বাংলাদেশে তৈরি হয় না। তাই সরকার আন্তর্জাতিক দরপত্র ডাকল এবং জাপানের কোম্পানি কাজ পেল।</div>

                    <h3>২. লেটার অফ ক্রেডিট (Letter of Credit - L/C)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> আন্তর্জাতিক বাণিজ্যে মূল্য পরিশোধের ক্ষেত্রে ব্যাংকের দেওয়া নিশ্চয়তাপত্র বা গ্যারান্টি।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> ব্যাংক নিশ্চয়তা দেয় যে বিক্রেতা পণ্য জাহাজে তুলে দিলেই তাকে টাকা পরিশোধ করা হবে। এটি সবচেয়ে নিরাপদ মাধ্যম।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> চীন থেকে ডেঙ্গুর টেস্ট কিট কেনার সময় বাংলাদেশ ব্যাংক চীনের ব্যাংকে L/C খুলল, যাতে চীনা বিক্রেতা টাকা পাওয়ার বিষয়ে নিশ্চিন্ত থাকে।</div>`
                }
            ]
        },
        {
            title: "মডিউল ৮: দরপত্র প্রক্রিয়া (অধ্যায় ৮)",
            lessons: [
                {
                    title: "৮.১ ই-জিপি ও মূল্যায়ন",
                    content: `<h2>দরপত্র প্রক্রিয়া ও মূল্যায়ন</h2>
                    
                    <h3>১. ই-জিপি (e-GP) পোর্টাল</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> বাংলাদেশের সরকারি ক্রয় প্রক্রিয়া অনলাইনে স্বচ্ছতার সাথে সম্পাদনের জাতীয় ডিজিটাল ওয়েব পোর্টাল।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> টেন্ডার ডকুমেন্ট কেনা, জামানত জমা দেওয়া এবং দরপত্র সাবমিট করা—সবই অনলাইনে হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> একজন ঠিকাদার ঘরে বসেই তার ল্যাপটপ থেকে ই-জিপিতে দরপত্র দাখিল করলেন।</div>

                    <h3>২. দরপত্র খোলার কমিটি (TOC বাতিল)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> পিপিআর ২০২৫ ও নতুন ই-জিপি গাইডলাইন অনুযায়ী সিস্টেমে টেন্ডার স্বয়ংক্রিয়ভাবে (Auto-open) খোলে, তাই TOC (Tender Opening Committee) বাতিল করা হয়েছে।</p>

                    <h3>৩. দরপত্র মূল্যায়ন কমিটি (TEC)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> দরপত্র যাচাই-বাছাই করে সবচেয়ে যোগ্য ঠিকাদার নির্বাচনের জন্য গঠিত কমিটি।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> এতে কমপক্ষে ৫ জন (সাধারণত ৫-৭ জন) সদস্য থাকতে হয়, যার মধ্যে বাইরের দপ্তরের সদস্যও থাকেন।</p>`
                }
            ]
        },
        {
            title: "মডিউল ৯: জামানত ও গ্যারান্টি (অধ্যায় ৯)",
            lessons: [
                {
                    title: "৯.১ দরপত্র ও কার্যসম্পাদন জামানত",
                    content: `<h2>জামানতের ধরনসমূহ</h2>
                    
                    <h3>১. দরপত্র জামানত (Tender Security)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> টেন্ডার সাবমিট করার সময় ঠিকাদারকে ১-৩% টাকা জমা দিতে হয়, যাতে সে মাঝপথে পালিয়ে না যায়।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> এটি দরপত্রের বৈধতা মেয়াদের চেয়ে অতিরিক্ত ২৮ দিন বেশি বহাল থাকতে হয়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> রহিম সাহেব কাজ না পেয়েও যদি চুক্তি করতে অস্বীকৃতি জানায়, তবে তার এই জামানতের টাকা সরকার বাজেয়াপ্ত করবে।</div>

                    <h3>২. কার্যসম্পাদন জামানত (Performance Security)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> কাজ পাওয়ার পর চুক্তির আগে ঠিকাদারকে কাজ সঠিকভাবে সম্পন্ন করার গ্যারান্টি হিসেবে চুক্তিমূল্যের ৫-১০% জমা দিতে হয়।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> ঠিকাদার যদি অস্বাভাবিক কম দাম (SLT) দেয় (ফ্রন্ট লোডিং), তবে এই জামানত ২৫% পর্যন্ত হতে পারে।</p>

                    <h3>৩. রিটেনশন মানি (Retention Money)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> কাজ চলাকালে ঠিকাদারের প্রতিটি চলতি বিল থেকে ৫-১০% অর্থ কেটে রাখা হয়।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> কাজ শেষ হওয়ার পর ত্রুটি-বিচ্যুতি দায় মেয়াদের (DLP) (সাধারণত ১ বছর) পর কাজ ঠিক থাকলে এই টাকা ফেরত দেওয়া হয়।</p>`
                }
            ]
        },
        {
            title: "মডিউল ১০: চুক্তি ব্যবস্থাপনা (অধ্যায় ১০)",
            lessons: [
                {
                    title: "১০.১ ভেরিয়েশন, EOT ও LD",
                    content: `<h2>চুক্তি বাস্তবায়ন ও সমস্যা সমাধান</h2>
                    
                    <h3>১. ভেরিয়েশন অর্ডার (Variation Order)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> কাজের প্রয়োজনে চুক্তিতে থাকা কাজের পরিমাণ কমানো বা বাড়ানোর আনুষ্ঠানিক নির্দেশ।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> নতুন টেন্ডার না ডেকে প্রাথমিক ধাপে চুক্তিমূল্যের অনধিক ১৫% পর্যন্ত কাজ বাড়ানো যায়।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> ১০ কি.মি. রাস্তার কাজ চলার সময় দেখা গেল পাশে ১ কি.মি. সংযোগ সড়ক করা জরুরি। তখন ওই ঠিকাদারকেই ১৫% সীমার মধ্যে ভেরিয়েশন অর্ডার দিয়ে কাজটি করানো হলো।</div>

                    <h3>২. সময় বৃদ্ধি (EOT - Extension of Time)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> যৌক্তিক কারণে (যেমন প্রাকৃতিক দুর্যোগ) নির্দিষ্ট সময়ে কাজ শেষ করতে না পারলে ঠিকাদারকে জরিমানা ছাড়া কাজের মেয়াদ বাড়িয়ে দেওয়া।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> টানা ১৫ দিন বন্যার কারণে কাজ বন্ধ থাকায় ঠিকাদারের মেয়াদ ১৫ দিন বাড়ানো হলো।</div>

                    <h3>৩. বিলম্ব জনিত ক্ষতিপূরণ (LD - Liquidated Damages)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> ঠিকাদারের নিজের গাফিলতিতে কাজ দেরি হলে প্রতিদিনের জন্য নির্দিষ্ট হারে (০.১%) জরিমানা কাটা হয়, যা সর্বোচ্চ ১০% হতে পারে।</p>`
                }
            ]
        },
        {
            title: "মডিউল ১১: অভিযোগ ও আপিল (অধ্যায় ১১)",
            lessons: [
                {
                    title: "১১.১ অভিযোগ দায়ের ও আপিল প্যানেল",
                    content: `<h2>আইনি পদক্ষেপ</h2>
                    
                    <h3>১. অভিযোগ দায়ের</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> দরপত্রে অন্যায় বা বৈষম্য হলে ঠিকাদার প্রথমে ক্রয়কারী কার্যালয় প্রধান (HOPE) এর নিকট লিখিত অভিযোগ দায়ের করেন।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> HOPE কে নির্দিষ্ট সময়ের মধ্যে (যেমন ১৫ দিন) এর নিষ্পত্তি করতে হয়।</p>

                    <h3>২. আপিল বা রিভিউ প্যানেল</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> HOPE এর সিদ্ধান্তে সন্তুষ্ট না হলে ঠিকাদার নির্ধারিত ফি জমা দিয়ে স্বাধীন রিভিউ প্যানেলে আপিল করতে পারেন।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> রিভিউ প্যানেলে নিরপেক্ষ আইনজ্ঞ ও বিশেষজ্ঞরা থাকেন, তারা তদন্ত করে চূড়ান্ত রায় দেন।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> একজন ঠিকাদারকে অন্যায়ভাবে বাতিল করা হলে সে ৫,০০০ টাকা ফি দিয়ে রিভিউ প্যানেলে আপিল করল। প্যানেল প্রমাণ পেয়ে ঠিকাদারের পক্ষে রায় দিল।</div>`
                }
            ]
        },
        {
            title: "মডিউল ১২: নৈতিকতা ও শৃঙ্খলা (অধ্যায় ১২)",
            lessons: [
                {
                    title: "১২.১ কোড অফ এথিক্স ও ডিবারমেন্ট",
                    content: `<h2>নৈতিকতা ও শাস্তি</h2>
                    
                    <h3>১. কোড অফ এথিক্স (Code of Ethics)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> সরকারি ক্রয় প্রক্রিয়ার সাথে জড়িত কর্মকর্তা, ঠিকাদার ও পরামর্শকদের অবশ্য পালনীয় আচরণবিধি।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> দুর্নীতি, ঘুষ, জালিয়াতি এবং স্বার্থের সংঘাত সম্পূর্ণ নিষিদ্ধ।</p>

                    <h3>২. ডিবারমেন্ট (Debarment / অযোগ্য ঘোষণা)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> পেশাগত অসদাচরণ বা জালিয়াতির কারণে কোনো ঠিকাদারকে নির্দিষ্ট সময়ের জন্য সরকারি টেন্ডারে নিষিদ্ধ করা।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> পিপিআর-২০২৫ অনুযায়ী এটি <strong>'ডিবারমেন্ট রিভিউ বোর্ড'</strong> পরিচালনা করে।</p>
                    <div class='example-box'><strong>💡 বাস্তব উদাহরণ:</strong> এক ঠিকাদার ভুয়া ব্যাংক গ্যারান্টি জমা দেওয়ায় তাকে আগামী ৩ বছরের জন্য সব সরকারি টেন্ডারে ডিবার (কালোতালিকাভুক্ত) করা হলো।</div>

                    <h3>৩. প্রকৃত সুবিধাভোগী মালিক (Beneficial Owner)</h3>
                    <p class="definition-text"><span class="badge-def">সংজ্ঞা</span> বেনামী বা ভুয়া নামে কোম্পানি খুলে টেন্ডার নেওয়া ঠেকাতে মূল মালিকের তথ্য প্রকাশ।</p>
                    <p class="explanation-text"><span class="badge-exp">ব্যাখ্যা</span> পিপিআর-২০২৫ এ চুক্তি স্বাক্ষরের পূর্বে ঠিকাদারের প্রকৃত মালিকের তথ্য প্রকাশ বাধ্যতামূলক করা হয়েছে।</p>`
                }
            ]
        },
        {
            title: "মডিউল ১৩: তফসিলে অন্তর্ভুক্ত ফর্মসমূহ (Schedules)",
            lessons: [
                {
                    title: "১৩.১ তফসিল ১ থেকে ২১ এর সারাংশ",
                    content: `<h2>PPR-2025 এর ২১টি তফসিল (Schedules)</h2>
                    <p class="explanation-text">পিপিআর বিধিমালার সাথে ২১টি তফসিল যুক্ত আছে যেখানে সকল আদর্শ ফরম, ছক ও চুক্তিপত্র দেওয়া আছে।</p>
                    <ul>
                        <li><strong>তফসিল-১:</strong> পণ্য, কার্য ও সেবার আদর্শ দরপত্র দলিল বা STD (যেমন: PW3, PG4)।</li>
                        <li><strong>তফসিল-৩:</strong> প্রকিউরমেন্ট প্রসেসিং ও অ্যাপ্রুভাল প্রসিডিউর।</li>
                        <li><strong>তফসিল-৪:</strong> ক্রয় কৌশল উন্নয়ন (Procurement Strategy) ফরম্যাট।</li>
                        <li><strong>তফসিল-৫:</strong> বার্ষিক ক্রয় পরিকল্পনা (APP) ফরম্যাট।</li>
                        <li><strong>তফসিল-৭:</strong> মন্ত্রিসভা কমিটির জন্য প্রস্তাব প্রেরণ ছক (CCGP)।</li>
                        <li><strong>তফসিল-৮, ৯, ১০:</strong> কন্ট্রাক্ট অ্যাওয়ার্ড ও পাবলিক রিপোর্টিং (চুক্তির তথ্য ওয়েবসাইটে প্রকাশ)।</li>
                        <li><strong>তফসিল-১১:</strong> রেকর্ডস সংরক্ষণ নীতিমালা।</li>
                        <li><strong>তফসিল-১২:</strong> জয়েন্ট ভেঞ্চার (JVCA) চুক্তির নমুনা।</li>
                        <li><strong>তফসিল-১৩:</strong> পরামর্শকের স্বার্থের সংঘাত (Conflict of Interest) নিরূপণের ছক।</li>
                        <li><strong>তফসিল-১৪:</strong> প্রকিউরমেন্ট প্রক্রিয়ার ফ্লো-চার্টসমূহ।</li>
                        <li><strong>তফসিল-১৮:</strong> অস্বাভাবিক নিম্নমূল্যের (SLT) দরপত্র মূল্যায়নের গাণিতিক সূত্র ও পদ্ধতি।</li>
                        <li><strong>তফসিল-২০:</strong> নৈতিক আচরণবিধি (Code of Ethics)।</li>
                        <li><strong>তফসিল-২১:</strong> ডেবারমেন্ট রিভিউ বোর্ডের গঠন ও আপিল নিষ্পত্তি।</li>
                    </ul>`
                }
            ]
        }
    ];

    function renderModules() {
        const container = document.getElementById('module-container');
        learningModules.forEach(mod => {
            const card = document.createElement('div');
            card.className = 'module-card';
            const title = document.createElement('h3');
            title.innerText = mod.title;
            card.appendChild(title);

            mod.lessons.forEach(lesson => {
                const btn = document.createElement('button');
                btn.className = 'lesson-btn';
                btn.innerHTML = `${lesson.title} <span>📖</span>`;
                btn.onclick = () => openModal(lesson.content);
                card.appendChild(btn);
            });
            container.appendChild(card);
        });
    }

    const modal = document.getElementById('lesson-modal');
    function openModal(content) { document.getElementById('modal-body').innerHTML = content; modal.style.display = 'block'; }
    function closeModal() { modal.style.display = 'none'; }
    window.onclick = function(event) { if (event.target == modal) closeModal(); }
    window.onload = renderModules;


    // ================= MASSIVE QUESTION BANK (150+ QUESTIONS DEDUPLICATED) =================
    const masterQuestionBank = [
        // ---------- Mandatory Focus Topics (RFQ, OTM, QCBS, Framework, SSS, APP) ----------
        { qType: 'mcq', q: "জরুরি সাধারণ পণ্য কিনতে (সর্বোচ্চ ৫ লক্ষ টাকা পর্যন্ত) কমপক্ষে ৩ জনের কোটেশন নিয়ে কোন পদ্ধতি ব্যবহার করা হয়?", options: ["OTM", "RFQ (কোটেশন)", "LTM", "DPM"], a: 1 },
        { qType: 'mcq', q: "উন্মুক্ত দরপত্র পদ্ধতিতে (OTM) ৩ কোটি টাকার ঊর্ধ্বে অভ্যন্তরীণ পূর্ত কাজের (Works) জন্য কোন স্ট্যান্ডার্ড দরপত্র দলিল ব্যবহৃত হয়?", options: ["PW1", "PW2", "PW3", "PW4"], a: 2 },
        { qType: 'mcq', q: "পরামর্শক নিয়োগে গুণগত মান ও আর্থিক মূল্যের সমন্বয়ে (যেমন: ৮০:২০) কোন পদ্ধতিটি সবচেয়ে বেশি ব্যবহৃত হয়?", options: ["LCS", "QCBS", "SSS", "FBS"], a: 1 },
        { qType: 'mcq', q: "দাপ্তরিক স্টেশনারি বা প্রিন্টিংয়ের মতো বারবার প্রয়োজনীয় পণ্য বা সেবার জন্য পিপিআর অনুযায়ী কোন চুক্তি করা সুবিধাজনক?", options: ["লাম্প-সাম চুক্তি", "টার্ন-কি চুক্তি", "ফ্রেমওয়ার্ক চুক্তি (Framework Agreement)", "পার্সেন্টেজ চুক্তি"], a: 2 },
        { qType: 'mcq', q: "একক উৎসভিত্তিক পরামর্শক নির্বাচনের (SSS - Single Source Method) ক্ষেত্রে ব্যক্তি পরামর্শকের (Individual Consultant) জন্য সর্বাধিক আর্থিক সীমা কত?", options: ["৫ লক্ষ টাকা", "১০ লক্ষ টাকা", "১৫ লক্ষ টাকা", "২০ লক্ষ টাকা"], a: 1 },
        { qType: 'mcq', q: "e-GP সিস্টেমে APP (বার্ষিক ক্রয় পরিকল্পনা / Annual Procurement Plan) তৈরি করার দায়িত্ব মূলত কার?", options: ["Procuring Entity (PE)", "HOPE", "TEC", "BPPA"], a: 0 },

        // ---------- Basic Principles & Methods ----------
        { qType: 'mcq', q: "আউটসোর্সিংয়ের মাধ্যমে নিরাপত্তা প্রহরী (Security Guard) বা পরিচ্ছন্নতাকর্মী নিয়োগ কোন ধরনের ক্রয়ের অন্তর্ভুক্ত?", options: ["পণ্য (Goods)", "কার্য (Works)", "ভৌত সেবা (Physical Services)", "বুদ্ধিবৃত্তিক সেবা (Intellectual Services)"], a: 2 },
        { qType: 'mcq', q: "'এক ধাপ দুই খাম' (One Stage Two Envelope - OSTETM) পদ্ধতি প্রধানত কোন ক্ষেত্রে ব্যবহৃত হয়?", options: ["ছোট কোটেশনের ক্ষেত্রে", "জটিল কারিগরি পণ্য, বৃহৎ পূর্ত কাজ বা টার্ন-কি চুক্তির ক্ষেত্রে", "সরাসরি ক্রয়ের ক্ষেত্রে", "ফোর্স অ্যাকাউন্টের ক্ষেত্রে"], a: 1 },
        { qType: 'mcq', q: "জরুরি দুর্যোগ মোকাবিলায় বা রাষ্ট্রীয় অতিব জরুরি প্রয়োজনে প্রতিযোগিতামূলক দরপত্র এড়িয়ে দ্রুত পণ্য, কার্য বা সেবা ক্রয়ের জন্য কোন পদ্ধতি ব্যবহার করা হয়?", options: ["OTM", "RFQ", "LTM", "DPM (Direct Procurement Method)"], a: 3 },
        { qType: 'mcq', q: "'HOPE' (Head of Procuring Entity)-এর বাংলা পরিভাষা কী?", options: ["প্রকল্প পরিচালক", "ক্রয়কারী কার্যালয়ের প্রধান", "মূল্যায়ন কমিটির সভাপতি", "সচিব"], a: 1 },
        { qType: 'mcq', q: "টার্ন-কি (Turn key) চুক্তি বলতে কী বোঝায়?", options: ["শুধু নকশা প্রণয়ন", "নকশা-নির্মাণ-সরঞ্জাম ক্রয় ও স্থাপন করে চালু অবস্থায় হস্তান্তর", "শুধু পণ্য সরবরাহ", "শ্রমিক সরবরাহ"], a: 1 },
        { qType: 'mcq', q: "উন্মুক্ত দরপত্র পদ্ধতিতে (OTM) ১ (এক) কোটি টাকা পর্যন্ত ক্রয়ের ক্ষেত্রে দরপত্র দাখিলের ন্যূনতম সময়সীমা কত দিন?", options: ["৭ দিন", "১৪ দিন", "২১ দিন", "২৮ দিন"], a: 1 },
        
        // ---------- PPR-2025 Specific Updates ----------
        { qType: 'mcq', q: "'পাবলিক প্রকিউরমেন্ট বিধিমালা, ২০২৫' (PPR-2025) আনুষ্ঠানিকভাবে কবে থেকে কার্যকর হয়?", options: ["৪ মে ২০২৫", "২৮ সেপ্টেম্বর ২০২৫", "১ জুলাই ২০২৫", "৩১ ডিসেম্বর ২০২৫"], a: 1 },
        { qType: 'mcq', q: "নতুন পিপিআর-২০২৫ এ মোট কতটি বিধি ও তফসিল রয়েছে?", options: ["১৩০টি বিধি, ১৪টি তফসিল", "১৫৪টি বিধি, ২১টি তফসিল", "১২০টি বিধি, ১৮টি তফসিল", "১৫৪টি বিধি, ২২টি তফসিল"], a: 1 },
        { qType: 'mcq', q: "অভ্যন্তরীণ পূর্ত কাজের (National Works) ক্ষেত্রে কোন বিতর্কিত মূল্যসীমাটি (Price Cap) বাতিল করা হয়েছে?", options: ["±৫%", "±১০%", "±১৫%", "±২০%"], a: 1 },
        { qType: 'mcq', q: "অস্বাভাবিক নিম্নমূল্য (SLT) মূল্যায়নের গাণিতিক সূত্রে 'দাপ্তরিক প্রাক্কলিত মূল্যের' (Official estimate) ওয়েটেজ কত?", options: ["৫০%", "২০%", "৩০%", "১০%"], a: 1 },
        { qType: 'mcq', q: "অস্বাভাবিক নিম্নমূল্য (SLT) মূল্যায়নে 'ই-জিপি বাজারদরের' ওয়েটেজ কত?", options: ["২০%", "৩০%", "৪০%", "৫০%"], a: 1 },
        { qType: 'mcq', q: "সীমিত দরপত্র পদ্ধতির (LTM) ক্ষেত্রে পূর্ত কাজের (Works) নতুন সীমা কত টাকা নির্ধারণ করা হয়েছে?", options: ["৩ কোটি টাকা", "৫ কোটি টাকা", "১০ কোটি টাকা", "৫০ লক্ষ টাকা"], a: 1 },
        { qType: 'mcq', q: "সীমিত দরপত্র পদ্ধতির (LTM) ক্ষেত্রে পণ্য বা ভৌত সেবা ক্রয়ের ঊর্ধ্বসীমা কত?", options: ["২৫ লক্ষ টাকা", "৫০ লক্ষ টাকা", "৭৫ লক্ষ টাকা", "১ কোটি টাকা"], a: 1 },
        { qType: 'mcq', q: "দরপত্রের বৈধতার মেয়াদ (Tender Validity) বর্তমানে সর্বোচ্চ কত দিন পর্যন্ত বর্ধিত করা হয়েছে?", options: ["৬০-১২০ দিন", "৯০-১২০ দিন", "৬০-১৫০ দিন", "১২০-১৮০ দিন"], a: 2 },
        { qType: 'mcq', q: "বিনির্দেশ ও প্রাক্কলন কমিটিতে (Specification and Estimation Committee) সদস্য সংখ্যা কতজন হতে হবে?", options: ["২ থেকে ৩ জন", "৩ থেকে ৫ জন", "৫ থেকে ৭ জন", "৭ জনের বেশি"], a: 1 },
        { qType: 'mcq', q: "নিচের কোনটি পিপিআর-২০২৫ এ একটি সম্পূর্ণ পৃথক ক্রয় শ্রেণি (Distinct Category) হিসেবে স্বীকৃতি পেয়েছে?", options: ["পূর্ত কাজ", "ভৌত সেবা (Physical Services)", "পণ্য", "বুদ্ধিবৃত্তিক সেবা"], a: 1 },
        { qType: 'mcq', q: "সরকারি ক্রয়ে সম্পূর্ণ ডিজিটাল ফুটপ্রিন্ট নিশ্চিত করতে কোন বিধির অধীনে ই-জিপি পোর্টালে ডিজিটাল দরপত্র সম্পূর্ণ বাধ্যতামূলক করা হয়েছে?", options: ["বিধি ১৫০", "বিধি ১৪৯", "বিধি ১০৯", "বিধি ৩১"], a: 0 },
        { qType: 'mcq', q: "সংশোধিত ই-জিপি গাইডলাইন-২০২৫ অনুযায়ী, e-GP সিস্টেমে কোন কমিটির আর প্রয়োজন নেই বলে উল্লেখ করা হয়েছে?", options: ["দরপত্র মূল্যায়ন কমিটি (TEC)", "দরপত্র উন্মুক্তকরণ কমিটি (TOC)", "বিনির্দেশ ও প্রাক্কলন কমিটি", "ডিবারমেন্ট রিভিউ বোর্ড"], a: 1 },
        { qType: 'mcq', q: "নতুন ই-জিপি গাইডলাইন-২০২৫ এ ঠিকাদারদের পরিচয় যাচাই ও নিবন্ধনের জন্য কোন ডাটাবেসের সাথে সিস্টেম যুক্ত করা হয়েছে?", options: ["পাসপোর্ট ডাটাবেস", "জাতীয় পরিচয়পত্র (NID) ডাটাবেস", "ট্রেড লাইসেন্স ডাটাবেস", "টিআইএন (TIN) ডাটাবেস"], a: 1 },
        { qType: 'mcq', q: "সরাসরি নগদ ক্রয়ের (Direct Cash Purchase) ক্ষেত্রে প্রতি ক্রয়ের আর্থিক সীমা সর্বোচ্চ কত?", options: ["১০,০০০ টাকা", "১৫,০০০ টাকা", "২০,০০০ টাকা", "২৫,০০০ টাকা"], a: 3 },
        { qType: 'mcq', q: "সরাসরি নগদ ক্রয়ের ক্ষেত্রে বাৎসরিক মোট পরিমাণ সর্বোচ্চ কত হতে পারে?", options: ["৫ লক্ষ টাকা", "১০ লক্ষ টাকা", "১৫ লক্ষ টাকা", "২০ লক্ষ টাকা"], a: 1 },
        { qType: 'mcq', q: "চুক্তি সম্পাদনের নোটিশ বা NOA (Notification of Award) জারী করার সময়সীমা ক্রয়কারী কার্যালয় প্রধান কর্তৃক সিদ্ধান্ত গ্রহণের কত দিনের মধ্যে হতে হবে?", options: ["৩ দিন", "৫ দিন", "৭ দিন", "১০ দিন"], a: 2 },
        { qType: 'mcq', q: "ভেরিয়েশন অর্ডার (Variation Order) প্রণয়ন হতে অনুমোদন পর্যন্ত সর্বোচ্চ সময়সীমা কত দিন?", options: ["১৫ দিন", "২০ দিন", "৩০ দিন", "৪৫ দিন"], a: 2 },
        { qType: 'mcq', q: "প্রাক-দরপত্র সভার (Pre-tender meeting) কার্যবিবরণী সভা অনুষ্ঠিত হবার কত দিনের মধ্যে দরদাতাদের কাছে বিতরণ করতে হবে?", options: ["৩ দিন", "৫ দিন", "৭ দিন", "১০ দিন"], a: 1 },
        { qType: 'mcq', q: "পেশাগত অসদাচরণ ও ডিবারমেন্ট (Debarment) সংক্রান্ত বিধি পিপিআর-২০২৫ এর কত নম্বর বিধিতে বর্ণিত হয়েছে?", options: ["বিধি ৭১", "বিধি ৭২", "বিধি ১৪৯", "বিধি ১৫০"], a: 2 },
        { qType: 'mcq', q: "দরপত্র মূল্যায়ন কমিটিতে (TEC) সাধারণত কতজন সদস্য থাকে?", options: ["৩ থেকে ৫ জন", "৫ থেকে ৭ জন", "৭ থেকে ৯ জন", "নির্দিষ্ট কোনো সংখ্যা নেই"], a: 1 },
        { qType: 'mcq', q: "তালিকাভুক্তিকরণ কমিটিতে (Enlistment Committee) মোট কতজন সদস্য থাকে?", options: ["২ জন", "৩ জন", "৫ জন", "৭ জন"], a: 1 },
        { qType: 'mcq', q: "রিভিউ প্যানেলে (Review Panel) আইন বিষয়ক বিশেষজ্ঞের সংখ্যা সর্বাধিক কতজন হতে পারে?", options: ["৫ জন", "৭ জন", "১০ জন", "১৫ জন"], a: 2 },
        { qType: 'mcq', q: "দুই পর্যায় বিশিষ্ট দরপত্র পদ্ধতির (TSTM) দ্বিতীয় পর্যায়ের দরপত্র প্রণয়ন ও দাখিলের সময়সীমা কত দিন?", options: ["৭ দিন", "১৪ দিন", "২১ দিন", "২৮ দিন"], a: 2 },
        { qType: 'mcq', q: "ক্রয়কারী কর্তৃক দরপত্র দলিলের স্পষ্টীকরণ এবং সংশোধনী (addendum) জারী করিবার সময়সীমা কত?", options: ["৩ কার্যদিবস", "৫ কার্যদিবস", "৭ কার্যদিবস", "১০ কার্যদিবস"], a: 1 },
        { qType: 'mcq', q: "আউটসোর্সিং প্রক্রিয়ায় সেবা গ্রহণের জন্য নতুন কোন এসটিডি (STD) প্রবর্তন করা হয়েছে?", options: ["PS1", "PS2", "PS3 (Outsourcing)", "PS4"], a: 2 },
        { qType: 'mcq', q: "বুদ্ধিবৃত্তিক ও পেশাগত সেবার ক্ষেত্রে কার্য-সম্পাদন জামানত (Performance Security) কত শতাংশ?", options: ["১%-৩%", "৩%-৫%", "৫%-১০%", "১০%-১৫%"], a: 1 },
        { qType: 'mcq', q: "দরপত্র জামানত দাপ্তরিক প্রাক্কলিত মূল্যের সর্বাধিক কত শতাংশের মধ্যে নির্দিষ্ট করা হয়?", options: ["২%", "৩%", "৫%", "১০%"], a: 1 },
        { qType: 'mcq', q: "কার্য ও ভৌত সেবার চুক্তির ক্ষেত্রে রিটেনশন মানি (Retention Money) সর্বাধিক কত শতাংশ হতে পারে?", options: ["১০%", "১৫%", "২০%", "২৫%"], a: 3 },
        { qType: 'mcq', q: "জয়েন্ট ভেঞ্চার (JVCA) চুক্তির ক্ষেত্রে ব্যবহৃত নন-জুডিশিয়াল স্ট্যাম্পের মূল্যমান কত হতে হবে?", options: ["১০০ টাকা", "১৫০ টাকা", "৩০০ টাকা", "৫০০ টাকা"], a: 2 },
        { qType: 'mcq', q: "কোনো অভিযোগ পুনরীক্ষণের জন্য রিভিউ প্যানেলের সদস্য-প্রতি সভার সম্মানী ফি কত?", options: ["৩০০০ টাকা", "৫০০০ টাকা", "৭০০০ টাকা", "১০০০০ টাকা"], a: 1 },
        { qType: 'mcq', q: "ঠিকাদারদের তালিকাভুক্তি (Enlistment) নবায়ন ফি কত?", options: ["১০০০ টাকা", "২০০০ টাকা", "৩০০০ টাকা", "৫০০০ টাকা"], a: 1 },
        
        // ---------- Tofsil based MCQs ----------
        {qType:'mcq',q:"পিপিআর ২০২৫-এর তফসিল-১ মূলত কী নির্ধারণ করে?",options:["ক্রয়ের বাজেট","ক্রয় প্রক্রিয়ায় ব্যবহারযোগ্য আদর্শ দলিল","দরপত্র খোলার তারিখ","ঠিকাদার তালিকা"],a:1},
        {qType:'mcq',q:"তফসিল-১-এর আওতাভুক্ত নয় কোনটি?",options:["পণ্য ক্রয়","ভৌতসেবা ক্রয়","জমি অধিগ্রহণ","পেশাগত সেবা ক্রয়"],a:2},
        {qType:'mcq',q:"'ভৌতসেবা' (Physical Services) বলতে বোঝায়—",options:["পরামর্শক সেবা","নির্মাণ কাজ ও প্রকৌশল সেবা","অডিটিং সেবা","প্রশিক্ষণ সেবা"],a:1},
        {qType:'mcq',q:"'বুদ্ধিবৃত্তিক ও পেশাগত সেবা'-এর মধ্যে পড়ে—",options:["ইট সরবরাহ","অফিস ভাড়া","পরামর্শক সেবা (কনসালটেন্সি)","গাড়ি কেনা"],a:2},
        {qType:'mcq',q:"আদর্শ দলিল ব্যবহারের মূল উদ্দেশ্য কী?",options:["ক্রয় প্রক্রিয়ায় স্বচ্ছতা নিশ্চিত করা","দরপত্র জটিল করা","ঠিকাদার বাছাই কঠিন করা","মূল্য বৃদ্ধি করা"],a:0},
        {qType:'mcq',q:"পণ্য ক্রয়ের জন্য সাধারণত কোন টেন্ডার ফর্ম ব্যবহার করা হয়?",options:["তফসিল-১৭ (ক)","তফসিল-১৭ (খ)","তফসিল-১৭ (গ)","তফসিল-১৭ (ঘ)"],a:0},
        {qType:'mcq',q:"নির্মাণ কাজের জন্য কোন টেন্ডার ফর্ম প্রযোজ্য?",options:["তফসিল-১৭ (ক)","তফসিল-১৭ (খ)","তফসিল-১৬","তফসিল-১২"],a:1},
        {qType:'mcq',q:"তফসিল-২ মূলত কী নির্দেশ করে?",options:["পণ্যের গুণগত মান","প্রশাসনিক ও ক্রয় সংক্রান্ত পদক্ষেপের প্রক্রিয়া","দরদাতার বয়স","ঠিকাদারের লাইসেন্স"],a:1},
        {qType:'mcq',q:"'সময়সীমা' (Timeframe) নির্ধারণের মূল লক্ষ্য কী?",options:["কাজ ধীরগতিতে করা","কার্যক্রমের সময়সীমা ও প্রক্রিয়াগত শৃঙ্খলা নিশ্চিত করা","বিলম্বে দরপত্র আহ্বান","ঠিকাদার পরিবর্তন"],a:1},
        {qType:'mcq',q:"ক্রয় মূল্য নির্ধারণে কোন বিষয়টি গুরুত্বপূর্ণ?",options:["দরদাতার ইচ্ছা","প্রকৃত বাজার মূল্য","সরকারি কর্মকর্তার সিদ্ধান্ত","বিগত বছরের মূল্য"],a:1},
        {qType:'mcq',q:"দরপত্রের মেয়াদকাল সাধারণত কত দিন নির্ধারণ করা হয়? (সাধারণ নিয়ম)",options:["১৫ দিন","৩০-৪৫ দিন","৯০ দিন","১৮০ দিন"],a:2},
        {qType:'mcq',q:"তফসিল-৩-এর মূল উদ্দেশ্য কী?",options:["দরপত্র ডিজাইন করা","প্রক্রিয়াগত মানদণ্ড এবং অনুমোদন প্রক্রিয়ার জন্য নির্দেশিকা দেওয়া","ঠিকাদার তালিকা তৈরি","চুক্তি স্বাক্ষর"],a:1},
        {qType:'mcq',q:"দরপত্র খোলার সময় কারা উপস্থিত থাকতে পারেন?",options:["শুধু সরকারি কর্মকর্তা","দরদাতা বা তাদের প্রতিনিধি","পুলিশ","সাংবাদিক"],a:1},
        {qType:'mcq',q:"দরপত্র খোলার পর কোন তথ্য ঘোষণা করা হয়?",options:["দরদাতার ব্যক্তিগত ঠিকানা","দরপত্রের মূল্য ও সংশোধনী (যদি থাকে)","দরদাতার ব্যাংক ব্যালেন্স","পূর্ববর্তী চুক্তির তথ্য"],a:1},
        {qType:'mcq',q:"পণ্য ক্রয়ের দরপত্র মূল্যায়নে সাধারণত কয়টি ধাপ থাকে?",options:["১টি","২টি (প্রাথমিক ও চূড়ান্ত)","৩টি","৪টি"],a:1},
        {qType:'mcq',q:"তফসিল-৪ কীসের জন্য ব্যবহৃত হয়?",options:["দরপত্র ফরম","কার্যকর ক্রয় কৌশল প্রণয়ন ও প্রয়োগের টেমপ্লেট","চুক্তি নমুনা","ঠিকাদার তালিকা"],a:1},
        {qType:'mcq',q:"তফসিল-৫ কতটি অংশে বিভক্ত?",options:["২টি","৩টি","৪টি","৫টির অধিক"],a:3},
        {qType:'mcq',q:"উন্নয়ন প্রকল্পের মোট ক্রয় পরিকল্পনা (Total Procurement Plan) কে অনুমোদন করে?",options:["প্রকল্প পরিচালক","মন্ত্রী পরিষদ","পরিকল্পনা কমিশন/মন্ত্রণালয়","ঠিকাদার"],a:2},
        {qType:'mcq',q:"তফসিল-৬-এর বিষয়বস্তু কী?",options:["ক্রয় পরিকল্পনা","সময়সীমা ও ক্রয় প্রক্রিয়ার পর্যায়ক্রমিক রূপরেখা","দরপত্র ফরম","ঠিকাদার নিয়োগ"],a:1},
        {qType:'mcq',q:"তফসিল-৭ কীসের জন্য ব্যবহৃত হয়?",options:["দরপত্র আহ্বান","মন্ত্রিসভা কমিটির জন্য ক্রয় প্রস্তাব প্রেরণ ছক","ঠিকাদার নিয়োগ","চুক্তি বাতিল"],a:1},
        {qType:'mcq',q:"চুক্তি অ্যাওয়ার্ডের পর প্রকাশ্য রিপোর্টিং (Public Reporting) করার উদ্দেশ্য কী?",options:["স্বচ্ছতা নিশ্চিত করা","দুর্নীতি কমানো","জনগণের জানার অধিকার নিশ্চিত করা","ওপরের সবগুলো"],a:3},
        {qType:'mcq',q:"তফসিল-১০ সাধারণত কী সম্পর্কিত?",options:["দরপত্র ফরম","চুক্তি সম্পাদন সংক্রান্ত প্রতিবেদন (পাবলিক রিপোর্টিং)","ঠিকাদার নিবন্ধন","ব্যাংক গ্যারান্টি"],a:1},
        {qType:'mcq',q:"ক্রয় রেকর্ড সংরক্ষণের মূল উদ্দেশ্য কী?",options:["অডিট, পর্যালোচনা ও আইনি স্বচ্ছতা নিশ্চিত করা","অফিস সাজানো","কাগজ জমা করা","ঠিকাদারকে ভয় দেখানো"],a:0},
        {qType:'mcq',q:"ক্রয় রেকর্ড সাধারণত কত বছর সংরক্ষণ করতে হয়?",options:["১ বছর","৩ বছর","সরকারি রেকর্ড সংরক্ষণ নীতি অনুযায়ী (যেমন: ৫ বছর)","চিরস্থায়ী"],a:2},
        {qType:'mcq',q:"তফসিল-১২-এর মূল উপাদান কী?",options:["একক ঠিকাদার চুক্তি","যৌথ উদ্যোগে (JVCA) চুক্তির নমুনা","দরপত্র ফরম","ক্রয় পরিকল্পনা"],a:1},
        {qType:'mcq',q:"জেভি (JVCA) চুক্তিতে 'লিড পার্টনার'-এর ভূমিকা কী?",options:["ক্রয়কারী সংস্থার সাথে যোগাযোগ রক্ষা ও দায়িত্বে নেতৃত্ব দেওয়া","শুধু অর্থ সরবরাহ","শুধু জনসংযোগ","কোনো ভূমিকা নেই"],a:0},
        {qType:'mcq',q:"'কনসালট্যান্ট কনফ্লিক্টস অফ ইন্টারেস্ট' বলতে কী বোঝায়?",options:["পরামর্শকের ব্যক্তিগত স্বার্থ ও পেশাগত দায়িত্বের মধ্যে দ্বন্দ্ব","পরামর্শক ও ঠিকাদারের বন্ধুত্ব","পরামর্শকের অসুস্থতা","পরামর্শকের বিদেশ ভ্রমণ"],a:0},
        {qType:'mcq',q:"ফ্লো-চার্ট (তফসিল-১৪) ব্যবহারের মূল সুবিধা কী?",options:["প্রক্রিয়ার ধাপগুলো চিত্রের মাধ্যমে বোঝা যায়","জটিলতা বাড়ে","সময় নষ্ট হয়","কাগজ অপচয় হয়"],a:0},
        {qType:'mcq',q:"ফ্লো-চার্টে 'সিদ্ধান্ত গ্রহণ' বোঝাতে সাধারণত কোন চিহ্ন ব্যবহৃত হয়?",options:["আয়তক্ষেত্র","রম্বস (হীরক আকৃতি)","বৃত্ত","তীর"],a:1},
        {qType:'mcq',q:"সিগনিফিক্যান্টলি লো-প্রাইসড টেন্ডার (SLT) চিহ্নিত করার মূল উদ্দেশ্য কী?",options:["দরদাতাকে পুরস্কৃত করা","নিম্নমানের কাজ ঠেকানো ও স্বাভাবিক মূল্য নিশ্চিত করা","দরপত্র জটিল করা","সরকারি অর্থ সাশ্র"],a:1},
        {qType:'mcq',q:"পাবলিক প্রকিউরমেন্টে নৈতিক আচরণবিধি (কোড অফ এথিক্স) পালন করা কেন জরুরি?",options:["দুর্নীতি প্রতিরোধ ও স্বচ্ছতা নিশ্চিত করতে","দরদাতাদের ভয় দেখাতে","চুক্তি দ্রুত করতে","বাজেট কমাতে"],a:0},
        {qType:'mcq',q:"'ডিবারমেন্ট' বলতে কী বোঝায়?",options:["ঠিকাদারকে পুরস্কার দেওয়া","অনিয়মের জন্য ঠিকাদারকে সাময়িকভাবে সরকারি ক্রয় থেকে নিষিদ্ধ করা","নতুন ঠিকাদার নিয়োগ","চুক্তির মেয়াদ বাড়ানো"],a:1},
        {qType:'mcq',q:"ডিবারমেন্ট রিভিউ বোর্ডের কাজ কী?",options:["ডিবার করা ঠিকাদারদের আপিল পর্যালোচনা করা","নতুন ঠিকাদার নিয়োগ","দরপত্র আহ্বান","বাজেট প্রণয়ন"],a:0},

        // ---------- FIBs (Fill in the Blanks) ----------
        {qType:'fib',q:"BPPA এর পূর্ণরূপ হলো Bangladesh Public Procurement {blank}।",a:"Authority",hints:["Agency","Authority","Association"]},
        {qType:'fib',q:"চুক্তি সম্পাদনের নোটিশকে সংক্ষেপে {blank} বলা হয়।",a:"NOA",hints:["LOI","NOA","MOU"]},
        {qType:'fib',q:"সরকারি ক্রয়ে স্বচ্ছতা আনতে চুক্তি স্বাক্ষরের পূর্বে দরপদাতা প্রতিষ্ঠানের 'প্রকৃত সুবিধাভোগী মালিক' বা {blank} Owner এর সম্পূর্ণ তথ্য প্রকাশ বাধ্যতামূলক করা হয়েছে।",a:"Beneficial",hints:["Beneficial","Primary","Legal"]},
        {qType:'fib',q:"অসাধু ঠিকাদারদের কালোতালিকাভুক্ত করার প্রক্রিয়া পর্যালোচনার জন্য পিপিআর-২০২৫ এ Debarment {blank} Board গঠন করা হয়েছে।",a:"Review",hints:["Appeal","Review","Action"]},
        {qType:'fib',q:"নতুন ই-জিপি গাইডলাইন-২০২৫ অনুযায়ী, ই-জিপি সিস্টেমে এখন থেকে টেন্ডার {blank} কমিটি বা TOC আর থাকছে না।",a:"Opening",hints:["Evaluation","Opening","Approval"]},
        {qType:'fib',q:"দরপত্র জামানত সাধারণত দরপত্রের মেয়াদের চেয়ে {blank} দিন বেশি বহাল থাকে। (ইংরেজিতে সংখ্যা লিখুন)",a:"28",hints:["14","21","28"]},
        {qType:'fib',q:"পিপিআর-২০২৫ এর তফসিল-১৮ অনুযায়ী অস্বাভাবিক নিম্নমূল্যের দরপত্র বা {blank} চিহ্নিতকরণ ও মূল্যায়ন প্রক্রিয়া বর্ণিত হয়েছে।",a:"SLT",hints:["LTM","SLT","OTM"]},
        {qType:'fib',q:"প্রাক-যোগ্যতা (Pre-qualification) আবেদনপত্র প্রণয়নের জন্য আবেদনকারীদের কমপক্ষে {blank} দিন সময় দিতে হবে। (ইংরেজিতে সংখ্যা লিখুন)",a:"21",hints:["14","21","28"]},
        {qType:'fib',q:"পিপিআর-২০২৫ অনুযায়ী দরপত্র মূল্যায়ন কমিটিতে (Evaluation Committee) সভার বৈধতার জন্য ন্যূনতম {blank} জন সদস্যের উপস্থিতি আবশ্যক।",a:"3",hints:["2","3","5"]},
        {qType:'fib',q:"ফ্রেমওয়ার্ক চুক্তির (Framework Agreement) সর্বোচ্চ মেয়াদ সাধারণত {blank} বছর হয়ে থাকে।",a:"3",hints:["2","3","5"]},
        {qType:'fib',q:"পিপিআর-২০২৫ এর বিধি ২৪ অনুযায়ী বার্ষিক ক্রয় পরিকল্পনার (APP) পাশাপাশি একটি দীর্ঘমেয়াদী {blank} Strategy প্রস্তুত করা বাধ্যতামূলক।",a:"Procurement",hints:["Development","Procurement","Financial"]},
        {qType:'fib',q:"সরকারি ক্রয়ে নৈতিক আচরণবিধি (Code of Ethics) পিপিআর-২০২৫ এর তফসিল-{blank} এ দেওয়া আছে।",a:"20",hints:["18","20","21"]},
        {qType:'fib',q:"e-GP পোর্টালে PE এর পূর্ণরূপ হলো Procuring {blank}।",a:"Entity",hints:["Enterprise","Entity","Establishment"]},
        {qType:'fib',q:"দরপত্র মূল্যায়নের জন্য গঠিত কমিটিকে সংক্ষেপে {blank} বলা হয়।",a:"TEC",hints:["TOC","TEC","PEC"]},
        {qType:'fib',q:"বার্ষিক ক্রয় পরিকল্পনাকে সংক্ষেপে {blank} বলা হয়।",a:"APP",hints:["APP","PP","AP"]},
        {qType:'fib',q:"RFQ এর পূর্ণরূপ হলো Request For {blank}।",a:"Quotation",hints:["Quality","Query","Quotation"]},
        {qType:'fib',q:"ঠিকাদারের চলতি বিল থেকে কর্তনকৃত অর্থকে {blank} মানি বলা হয়। (ইংরেজিতে লিখুন)",a:"Retention",hints:["Security","Retention","Advance"]},

        // ---------- FLOWCHARTS / ORDERING ----------
        {qType:'order',q:"OTM (উন্মুক্ত দরপত্র) পদ্ধতির সাধারণ ফ্লোচার্টটি সঠিক ক্রমানুসারে সাজান:",steps:["দরপত্র দলিল প্রস্তুত ও অনুমোদন","দরপত্র বিজ্ঞপ্তি প্রকাশ","দরপত্র গ্রহণ ও উন্মুক্তকরণ","দরপত্র মূল্যায়ন","চুক্তি স্বাক্ষর"]},
        {qType:'order',q:"পিপিআর-২০২৫ অনুযায়ী দরপত্র বাতিলের সিদ্ধান্ত গ্রহণের ধাপগুলো সাজান:",steps:["কারণ চিহ্নিতকরণ (যেমন: অস্বাভাবিক দর, অনিয়ম)","মূল্যায়ন কমিটির সুপারিশ","অনুমোদনকারী কর্তৃপক্ষের অনুমোদন","দরপত্র বাতিলের বিজ্ঞপ্তি প্রকাশ","নতুন দরপত্র আহ্বানের সিদ্ধান্ত"]},
        {qType:'order',q:"পরামর্শক নিয়োগের (QCBS) ধাপগুলো সাজান:",steps:["EOI আহ্বান ও সংক্ষিপ্ত তালিকা (Shortlist) তৈরি","RFP (Request for Proposal) ইস্যু","Technical Proposal মূল্যায়ন","Financial Proposal মূল্যায়ন ও কম্বাইন্ড স্কোরিং","দর কষাকষি (Negotiation) ও চুক্তি"]},
        {qType:'order',q:"সরাসরি ক্রয় পদ্ধতি (DPM) এর মাধ্যমে জরুরি ক্রয়ের ধাপগুলো সাজান:",steps:["জরুরি চাহিদা নিরূপণ ও HOPE এর অনুমোদন","নির্দিষ্ট ঠিকাদার/সরবরাহকারীর নিকট প্রস্তাব আহ্বান","প্রস্তাব গ্রহণ ও নেগোসিয়েশন","চুক্তি অনুমোদন","কার্যাদেশ প্রদান"]},
        {qType:'order',q:"নৈতিক আচরণবিধি লঙ্ঘনের অভিযোগ নিষ্পত্তির ধাপগুলো সাজান:",steps:["অভিযোগ দায়ের","তদন্ত কমিটি গঠন","অভিযুক্তের বক্তব্য গ্রহণ","প্রমাণ সংগ্রহ ও সাক্ষ্য গ্রহণ","চূড়ান্ত সিদ্ধান্ত ও শাস্তি ঘোষণা"]},
        {qType:'order',q:"e-GP তে ঠিকাদার কর্তৃক দরপত্র দাখিলের ধাপগুলো সাজান:",steps:["Tender Document Fee প্রদান","Tender Document ডাউনলোড","দরপত্রের ফর্ম ও BOQ পূরণ","Tender Security দাখিল","Final Submit"]},
        {qType:'order',q:"আন্তর্জাতিক পণ্য ক্রয়ের (ICT - Goods) এবং L/C প্রক্রিয়ার ধাপসমূহ সাজান:",steps:["NOA ইস্যু ও চুক্তি স্বাক্ষর","L/C (Letter of Credit) খোলা","Pre-shipment Inspection (প্রযোজ্য ক্ষেত্রে)","পণ্য জাহাজীকরণ ও রিসিভ","পেমেন্ট ক্লিয়ারেন্স"]},
        {qType:'order',q:"ফ্রেমওয়ার্ক চুক্তি (Framework Agreement) এর মাধ্যমে রুটিন পণ্য/সেবা ক্রয়ের ধাপসমূহ সাজান:",steps:["দীর্ঘমেয়াদি চাহিদা নিরূপণ ও দরপত্র আহ্বান","ফ্রেমওয়ার্ক চুক্তি স্বাক্ষর","কল-অফ অর্ডার (Call-off Order) প্রদান","পণ্য/সেবা সরবরাহ","বিল পরিশোধ"]},
        {qType:'order',q:"কোটেশন (RFQ) পদ্ধতিতে ছোট পণ্য বা সেবা ক্রয়ের ধাপগুলো সাজান:",steps:["কোটেশন আহ্বান","কোটেশন দাখিল ও গ্রহণ","TQEC দ্বারা মূল্যায়ন ও সুপারিশ","HOPE বা ক্ষমতাপ্রাপ্ত কর্মকর্তা কর্তৃক অনুমোদন","কার্যাদেশ (Work Order) প্রদান"]},
        {qType:'order',q:"OSTETM (এক ধাপ দুই খাম) পদ্ধতিতে বৃহৎ পণ্য/পূর্ত কাজের মূল্যায়নের ধাপগুলো সাজান:",steps:["দরপত্র আহ্বান","Technical ও Financial খাম একসাথে দাখিল","শুধুমাত্র Technical খাম উন্মুক্তকরণ ও মূল্যায়ন","উত্তীর্ণদের Financial খাম উন্মুক্তকরণ ও মূল্যায়ন","চুক্তি স্বাক্ষর"]},
        {qType:'order',q:"e-GP সিস্টেমে APP (বার্ষিক ক্রয় পরিকল্পনা) তৈরির ধাপগুলো সাজান:",steps:["APP Create","Workflow Assign","Submit to Approver","Approve APP","Publish APP"]}
    ];

    let currentQuestions = [];
    let currentQuestionIndex = 0;
    let userAnswers = [];
    let timerInterval;
    let timeLeft = 3600; 
    let questionTimeLeft = 180; 
    let isTestActive = false; 
    const totalQuestionsToAsk = 60;

    document.addEventListener("visibilitychange", function() {
        if (document.hidden && isTestActive) {
            forceTimeout("পরীক্ষা চলাকালে অন্য ট্যাবে যাওয়া বা ব্রাউজার মিনিমাইজ করা সম্পূর্ণ নিষেধ!");
        }
    });

    function forceTimeout(reasonMsg) {
        isTestActive = false;
        clearInterval(timerInterval);
        alert("🚨 টাইম-আউট / নিয়ম লঙ্ঘন!\n\n" + reasonMsg + "\n\nআপনার পরীক্ষাটি বাতিল করা হলো। পুনরায় টেস্ট শুরু করুন।");
        location.reload(); 
    }

    function shuffleArray(array) {
        let arr = [...array];
        for (let i = arr.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [arr[i], arr[j]] = [arr[j], arr[i]];
        }
        return arr;
    }

    function formatTime(seconds) {
        const m = Math.floor(seconds / 60).toString().padStart(2, '0');
        const s = (seconds % 60).toString().padStart(2, '0');
        return `${m}:${s}`;
    }

    // Smart Selection Algorithm
    function selectSmartQuestions() {
        const mandatoryKeywords = [
            ["RFQ", "কোটেশন"],
            ["OTM", "উন্মুক্ত দরপত্র"],
            ["QCBS"],
            ["ফ্রেমওয়ার্ক", "Framework"],
            ["SSS", "একক উৎস"],
            ["APP", "বার্ষিক ক্রয় পরিকল্পনা"]
        ];
        
        let selected = [];
        let remaining = [...masterQuestionBank];
        
        // 1. Pick at least one for each mandatory category without duplicating
        mandatoryKeywords.forEach(keywords => {
            const index = remaining.findIndex(q => {
                const qText = JSON.stringify(q).toLowerCase();
                return keywords.some(kw => qText.includes(kw.toLowerCase()));
            });
            if (index !== -1) {
                selected.push(remaining[index]);
                remaining.splice(index, 1); // Splice ensures no exact duplicate is picked later
            }
        });
        
        // 2. Fill the rest up to 60 with random questions from the remaining pool
        remaining = shuffleArray(remaining);
        const needed = totalQuestionsToAsk - selected.length;
        selected = selected.concat(remaining.slice(0, needed));
        
        // 3. Final shuffle so mandatory questions aren't predictably at the beginning
        return shuffleArray(selected);
    }

    function startTest() {
        // Smart select exact 60 questions
        currentQuestions = selectSmartQuestions();

        // Shuffle flowchart options
        currentQuestions.forEach(q => {
            if (q.qType === 'order') {
                q.shuffledSteps = shuffleArray(q.steps);
            }
        });

        userAnswers = currentQuestions.map(q => {
            if (q.qType === 'mcq') return null;
            if (q.qType === 'fib') return "";
            if (q.qType === 'order') return new Array(q.steps.length).fill("");
        });

        document.getElementById('start-screen').classList.add('hidden');
        document.getElementById('quiz-screen').classList.remove('hidden');
        
        currentQuestionIndex = 0;
        timeLeft = 3600; 
        isTestActive = true; 
        
        startTimer();
        loadQuestion();
    }

    function startTimer() {
        document.getElementById('time-left').innerText = formatTime(timeLeft);
        document.getElementById('q-time-left').innerText = formatTime(questionTimeLeft);
        
        timerInterval = setInterval(() => {
            timeLeft--;
            questionTimeLeft--;

            document.getElementById('time-left').innerText = formatTime(timeLeft);
            document.getElementById('q-time-left').innerText = formatTime(questionTimeLeft);
            
            if (questionTimeLeft <= 0) {
                forceTimeout("আপনি একটি প্রশ্নের উত্তর দেওয়ার জন্য ৩ মিনিটের বেশি সময় নিয়েছেন।");
                return;
            }

            if (timeLeft <= 0) {
                clearInterval(timerInterval);
                submitTest();
            }
        }, 1000);
    }

    function loadQuestion() {
        questionTimeLeft = 180; 
        document.getElementById('q-time-left').innerText = formatTime(questionTimeLeft);

        const qData = currentQuestions[currentQuestionIndex];
        
        document.getElementById('current-q-num').innerText = currentQuestionIndex + 1;
        document.getElementById('total-q-count').innerText = currentQuestions.length;
        document.getElementById('question-text').innerText = qData.q;
        
        const badge = document.getElementById('q-type-badge');
        const container = document.getElementById('answer-container');
        const hintBtn = document.getElementById('hint-btn');
        
        container.innerHTML = '';
        hintBtn.disabled = false;
        hintBtn.classList.remove('hidden');

        if (qData.qType === 'mcq') {
            badge.innerText = "MCQ (বহুনির্বাচনি)";
            badge.style.background = "#3498db";
            
            const optionsDiv = document.createElement('div');
            optionsDiv.className = 'options';
            optionsDiv.id = 'mcq-options';
            
            qData.options.forEach((opt, index) => {
                const label = document.createElement('label');
                const radio = document.createElement('input');
                radio.type = 'radio';
                radio.name = 'option';
                radio.value = index;
                
                if (userAnswers[currentQuestionIndex] === index) radio.checked = true;
                
                radio.addEventListener('change', (e) => {
                    userAnswers[currentQuestionIndex] = parseInt(e.target.value);
                });

                label.appendChild(radio);
                label.appendChild(document.createTextNode(opt));
                optionsDiv.appendChild(label);
            });
            container.appendChild(optionsDiv);

        } else if (qData.qType === 'fib') {
            badge.innerText = "Fill in the Blanks (শূন্যস্থান পূরণ)";
            badge.style.background = "#e67e22";
            
            const parts = qData.q.split('{blank}');
            const textEl = document.getElementById('question-text');
            textEl.innerHTML = ''; 
            
            textEl.appendChild(document.createTextNode(parts[0]));
            
            const input = document.createElement('input');
            input.type = 'text';
            input.className = 'fib-input';
            input.id = 'fib-input-field';
            input.placeholder = "উত্তর লিখুন";
            
            if(userAnswers[currentQuestionIndex]) {
                input.value = userAnswers[currentQuestionIndex];
            }
            
            input.addEventListener('input', (e) => {
                userAnswers[currentQuestionIndex] = e.target.value;
            });
            textEl.appendChild(input);
            
            if (parts[1]) textEl.appendChild(document.createTextNode(parts[1]));

        } else if (qData.qType === 'order') {
            badge.innerText = "Flowchart (ধাপ মেলানো)";
            badge.style.background = "#8e44ad";
            
            qData.steps.forEach((_, stepIndex) => {
                const stepDiv = document.createElement('div');
                stepDiv.className = 'order-step-container';
                
                const label = document.createElement('div');
                label.className = 'order-step-label';
                label.innerText = `ধাপ ${stepIndex + 1}:`;
                
                const select = document.createElement('select');
                select.className = 'order-select';
                
                const defaultOpt = document.createElement('option');
                defaultOpt.value = "";
                defaultOpt.innerText = "--- সঠিক ধাপটি নির্বাচন করুন ---";
                select.appendChild(defaultOpt);
                
                qData.shuffledSteps.forEach(optText => {
                    const opt = document.createElement('option');
                    opt.value = optText;
                    opt.innerText = optText;
                    select.appendChild(opt);
                });

                select.addEventListener('change', (e) => {
                    userAnswers[currentQuestionIndex][stepIndex] = e.target.value;
                });
                
                stepDiv.appendChild(label);
                stepDiv.appendChild(select);
                container.appendChild(stepDiv);
            });
        }

        if (currentQuestionIndex === currentQuestions.length - 1) {
            document.getElementById('next-btn').classList.add('hidden');
            document.getElementById('submit-btn').classList.remove('hidden');
        } else {
            document.getElementById('next-btn').classList.remove('hidden');
            document.getElementById('submit-btn').classList.add('hidden');
        }
    }

    function useHint() {
        const qData = currentQuestions[currentQuestionIndex];
        const hintBtn = document.getElementById('hint-btn');
        const container = document.getElementById('answer-container');
        
        if (qData.qType === 'mcq') {
            let wrongIndices = [];
            const userSelection = userAnswers[currentQuestionIndex];
            
            qData.options.forEach((opt, idx) => {
                if (idx !== qData.a && idx !== userSelection) wrongIndices.push(idx);
            });
            
            if (wrongIndices.length > 0) {
                let randomWrongIdx = wrongIndices[Math.floor(Math.random() * wrongIndices.length)];
                const labels = document.querySelectorAll('#mcq-options label');
                if(labels[randomWrongIdx]) labels[randomWrongIdx].style.display = 'none';
            }
            hintBtn.disabled = true;
            
        } else if (qData.qType === 'fib') {
            const hintContainer = document.createElement('div');
            hintContainer.className = 'fib-hints-box';
            hintContainer.innerHTML = '<strong>💡 সম্ভাব্য উত্তরসমূহ:</strong> <br><br>';
            
            let shuffledHints = shuffleArray(qData.hints);
            shuffledHints.forEach(hint => {
                const hintBadge = document.createElement('span');
                hintBadge.className = 'fib-hint-badge';
                hintBadge.innerText = hint;
                
                hintBadge.onclick = () => {
                    const inputField = document.getElementById('fib-input-field');
                    if(inputField) {
                        inputField.value = hint;
                        userAnswers[currentQuestionIndex] = hint;
                    }
                };
                hintContainer.appendChild(hintBadge);
            });
            
            container.appendChild(hintContainer);
            hintBtn.disabled = true;

        } else if (qData.qType === 'order') {
            const correctFirstStep = qData.steps[0];
            const firstSelect = document.querySelectorAll('.order-select')[0];
            
            if (firstSelect) {
                firstSelect.value = correctFirstStep;
                userAnswers[currentQuestionIndex][0] = correctFirstStep;
                firstSelect.style.backgroundColor = '#eafaf1';
                firstSelect.style.borderColor = '#2ecc71';
                firstSelect.style.color = '#27ae60';
                firstSelect.style.fontWeight = 'bold';
                firstSelect.disabled = true;
            }
            hintBtn.disabled = true;
        }
    }

    function nextQuestion() {
        if (currentQuestionIndex < currentQuestions.length - 1) {
            currentQuestionIndex++;
            loadQuestion();
        }
    }

    function submitTest() {
        isTestActive = false; 
        clearInterval(timerInterval);
        document.getElementById('quiz-screen').classList.add('hidden');
        document.getElementById('result-screen').classList.remove('hidden');
        calculateAndShowResults();
    }

    function calculateAndShowResults() {
        let score = 0;
        const totalQ = currentQuestions.length;
        const reviewContainer = document.getElementById('review-container');
        reviewContainer.innerHTML = '';

        currentQuestions.forEach((q, index) => {
            const userAns = userAnswers[index];
            let isCorrect = false;
            let isUnanswered = false;
            let userAnswerText = "";
            let correctAnswerText = "";

            if (q.qType === 'mcq') {
                isUnanswered = userAns === null;
                isCorrect = userAns === q.a;
                userAnswerText = isUnanswered ? "উত্তর দেননি" : q.options[userAns];
                correctAnswerText = q.options[q.a];
            } 
            else if (q.qType === 'fib') {
                isUnanswered = userAns.trim() === "";
                isCorrect = userAns.trim().toLowerCase() === q.a.trim().toLowerCase();
                userAnswerText = isUnanswered ? "উত্তর দেননি" : userAns;
                correctAnswerText = q.a;
            } 
            else if (q.qType === 'order') {
                const userArr = userAns;
                isUnanswered = userArr.every(v => v === "");
                isCorrect = userArr.length === q.steps.length && userArr.every((val, i) => val === q.steps[i]);
                userAnswerText = isUnanswered ? "উত্তর দেননি" : "<br>" + userArr.map((v, i) => `ধাপ ${i+1}: ${v || '[খালি]'}`).join("<br>");
                correctAnswerText = "<br>" + q.steps.map((v, i) => `ধাপ ${i+1}: ${v}`).join("<br>");
            }

            if (isCorrect) score++;

            const resultDiv = document.createElement('div');
            let statusClass = isCorrect ? 'correct-ans' : (isUnanswered ? 'unanswered' : 'wrong-ans');
            resultDiv.className = `result-item ${statusClass}`;
            let qTextClean = q.qType === 'fib' ? q.q.replace('{blank}', '_____') : q.q;

            let html = `<strong style="font-size: 20px; color: #2c3e50;">প্রশ্ন ${index + 1}: ${qTextClean}</strong><br><br>`;
            
            if (isCorrect) {
                html += `<span style="color: #27ae60; font-weight: bold;">✅ আপনার উত্তর (সঠিক): ${userAnswerText}</span>`;
            } else if (isUnanswered) {
                html += `<span style="color: #d35400; font-weight: bold;">⚠️ আপনি উত্তর দেননি।</span><br><br>`;
                html += `<span style="color: #27ae60; font-weight: bold;">✅ সঠিক উত্তর: ${correctAnswerText}</span>`;
            } else {
                html += `<span style="color: #c0392b; font-weight: bold;">❌ আপনার উত্তর: ${userAnswerText}</span><br><br>`;
                html += `<span style="color: #27ae60; font-weight: bold;">✅ সঠিক উত্তর: ${correctAnswerText}</span>`;
            }

            resultDiv.innerHTML = html;
            reviewContainer.appendChild(resultDiv);
        });

        const percentage = Math.round((score / totalQ) * 100);
        let remarks = "";
        if(percentage >= 80) remarks = "অসাধারণ! আপনার প্রকিউরমেন্ট জ্ঞান অত্যন্ত প্রখর। 🏆";
        else if(percentage >= 60) remarks = "খুব ভালো! আপনার বেসিক ভালো, তবে লার্নিং জোন থেকে আরেকটু শিখতে পারেন। 👍";
        else remarks = "আপনার বিধিমালা নিয়ে আরও পড়াশোনার প্রয়োজন আছে। 📚";

        document.getElementById('score-display').innerHTML = `
            স্কোর: ${score} / ${totalQ} (${percentage}%) <br>
            <span style="font-size: 22px; color: #7f8c8d; display:block; margin-top: 10px;">${remarks}</span>
        `;
    }
</script>

</body>
</html>

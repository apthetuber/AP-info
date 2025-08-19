<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Apurbo Islam (AP) • Socials</title>
    <!--
      This is a single-file responsive HTML app for "Apurbo Islam (AP)" social links.
      The theme is updated to be more professional and premium with improved
      design elements, animations, and typography.
      
      This version includes new features powered by the Gemini API:
      1. A bio generator that creates a professional bio based on the user's social links.
      2. A Text-to-Speech (TTS) feature to read the generated bio aloud.
    -->
    <!-- Font Awesome for social media icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    
    <style>
        /* --- General Styles (সাধারণ স্টাইল) --- */
        :root {
            --dark-bg: #0d0d0d;
            --card-bg: rgba(25, 25, 25, 0.7);
            --orange-main: #FF6700;
            --text-light: #f0f0f0;
            --text-muted: #bbb;
            --shadow-soft: 0 4px 20px rgba(0, 0, 0, 0.5);
            --border-radius-card: 20px;
            
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
            color: var(--text-light);
            background-color: var(--dark-bg);
            background-image:
                radial-gradient(circle at top left, var(--orange-main) 0%, transparent 35%),
                radial-gradient(circle at bottom right, var(--orange-main) 0%, transparent 35%);
            background-size: 100% 100%;
            background-repeat: no-repeat;
            background-attachment: fixed;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            padding: 20px;
            box-sizing: border-box;
            line-height: 1.6;
            animation: background-pulse 10s infinite alternate;
        }
        body { margin: 0; }

        @keyframes background-pulse {
            from { background-size: 100% 100%; }
            to { background-size: 110% 110%; }
        }

        /* --- Main Layout & Header (মূল লেআউট ও হেডার) --- */
        .container {
            max-width: 600px;
            margin: 0 auto;
            width: 100%;
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
            align-items: center;
            text-align: center;
        }
        .header {
            padding: 2rem 0;
            margin-bottom: 1rem;
        }
        .header h1 {
            font-size: clamp(2rem, 5vw, 3.5rem);
            margin: 0;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
            color: var(--text-light);
        }
        .header p {
            font-size: clamp(1rem, 3vw, 1.5rem);
            color: var(--text-muted);
            margin: 0.5rem 0 0;
        }

        /* --- Profile Picture (প্রোফাইল ছবি) --- */
        .profile-picture {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 5px solid var(--orange-main);
            box-shadow: 0 0 20px var(--orange-main), 0 0 40px rgba(255, 103, 0, 0.4);
            object-fit: cover;
            transition: transform 0.3s ease-in-out;
            margin-bottom: 1rem;
        }
        .profile-picture:hover {
            transform: scale(1.05) rotate(3deg);
            cursor: pointer;
        }

        /* --- Social Link Cards (সোশ্যাল লিংক কার্ড) --- */
        .social-card {
            background: var(--card-bg);
            border-radius: var(--border-radius-card);
            box-shadow: var(--shadow-soft);
            backdrop-filter: blur(15px);
            padding: 1.5rem;
            width: 100%;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
            text-decoration: none;
            color: var(--text-light);
            display: flex;
            align-items: center;
            gap: 1.5rem;
            animation: slide-in 0.5s ease-out forwards;
        }
        .social-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.8);
        }

        /* --- Icons (আইকন) --- */
        .social-icon-wrapper {
            background-color: var(--orange-main);
            color: var(--dark-bg);
            width: 50px;
            height: 50px;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 50%;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease-in-out;
        }
        .social-card:hover .social-icon-wrapper {
            transform: scale(1.1);
        }
        .social-icon {
            font-size: 1.8rem;
        }

        /* --- Text within Card (কার্ডের ভেতরের টেক্সট) --- */
        .card-text {
            display: flex;
            flex-direction: column;
            text-align: left;
        }
        .card-text .title {
            font-size: 1.2rem;
            font-weight: bold;
            color: var(--orange-main);
            transition: color 0.3s ease-in-out;
        }
        .social-card:hover .card-text .title {
            color: var(--text-light);
        }
        .card-text .link-text {
            font-size: 0.9rem;
            color: var(--text-muted);
            transition: color 0.3s ease-in-out;
        }
        .social-card:hover .card-text .link-text {
            color: var(--text-light);
        }

        /* --- New Gemini Feature Card --- */
        .gemini-card {
            display: flex;
            flex-direction: column;
            gap: 1rem;
            background: var(--card-bg);
            border-radius: var(--border-radius-card);
            box-shadow: var(--shadow-soft);
            backdrop-filter: blur(15px);
            padding: 1.5rem;
            width: 100%;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
        }
        .gemini-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.6);
        }
        .gemini-card h3 {
            margin: 0;
            color: var(--orange-main);
            font-size: 1.5rem;
        }
        .gemini-card .bio-output {
            background: rgba(255, 255, 255, 0.05);
            padding: 1rem;
            border-radius: 10px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            min-height: 80px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-muted);
            font-style: italic;
            text-align: center;
        }
        .gemini-card .button-group {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }
        .gemini-card button {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 10px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.1s;
        }
        .gemini-card button#generate-bio-btn {
            background-color: var(--orange-main);
            color: var(--dark-bg);
        }
        .gemini-card button#generate-bio-btn:hover {
            background-color: #e55c00;
        }
        .gemini-card button#listen-btn {
            background-color: #34495e;
            color: var(--text-light);
        }
        .gemini-card button#listen-btn:hover {
            background-color: #2c3e50;
        }
        .loading-spinner {
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            border-top: 4px solid var(--orange-main);
            width: 30px;
            height: 30px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>

    <!-- Main container (মূল কন্টেইনার) -->
    <div class="container">
        <!-- Profile & Header Section (প্রোফাইল ও হেডার অংশ) -->
        <div class="header">
            <!-- Profile picture with professional text -->
            <img src="https://placehold.co/150x150/ff6700/000000?text=AP" alt="Profile Picture" class="profile-picture">
            <h1>Apurbo Islam (AP)</h1>
            <p>আমাদের সব সোশ্যাল অ্যাকাউন্টস!</p>
        </div>

        <!-- Gemini API Feature Card -->
        <div class="gemini-card">
            <h3>আপনার সম্পর্কে জানুন ✨</h3>
            <div id="bio-output" class="bio-output">
                আপনার বায়ো তৈরি করতে নিচের বাটনে ক্লিক করুন!
            </div>
            <div class="button-group">
                <button id="generate-bio-btn">বায়ো জেনারেট করুন ✨</button>
                <button id="listen-btn" style="display:none;">শুনুন 🔊</button>
            </div>
        </div>

        <!-- Social Links Section (সোশ্যাল লিংকস অংশ) -->
        <a href="https://youtube.com/@ap-takunation?si=3GSIPxYzZU6VFS5G" class="social-card" target="_blank">
            <div class="social-icon-wrapper">
                <i class="fab fa-youtube social-icon"></i>
            </div>
            <div class="card-text">
                <span class="title">YouTube Channel</span>
                <span class="link-text">@ap-takunation</span>
            </div>
        </a>

        <a href="https://www.facebook.com/share/19bfJbZ1iE/" class="social-card" target="_blank">
            <div class="social-icon-wrapper">
                <i class="fab fa-facebook-f social-icon"></i>
            </div>
            <div class="card-text">
                <span class="title">Facebook Profile</span>
                <span class="link-text">ap-takunation</span>
            </div>
        </a>
        
        <a href="https://www.facebook.com/share/16oAvB1XMC/" class="social-card" target="_blank">
            <div class="social-icon-wrapper">
                <i class="fab fa-facebook social-icon"></i>
            </div>
            <div class="card-text">
                <span class="title">Facebook Page</span>
                <span class="link-text">ap-taku-page</span>
            </div>
        </a>

        <a href="https://www.tiktok.com/@clone.ap?_t=ZS-8yzyY6q23Cn&_r=1" class="social-card" target="_blank">
            <div class="social-icon-wrapper">
                <i class="fab fa-tiktok social-icon"></i>
            </div>
            <div class="card-text">
                <span class="title">TikTok</span>
                <span class="link-text">@clone.ap</span>
            </div>
        </a>

        <a href="https://www.instagram.com/ap_._sui/profilecard/?igsh=bWZybTlvZnZkcmdp" class="social-card" target="_blank">
            <div class="social-icon-wrapper">
                <i class="fab fa-instagram social-icon"></i>
            </div>
            <div class="card-text">
                <span class="title">Instagram</span>
                <span class="link-text">@ap_._sui</span>
            </div>
        </a>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const bioOutput = document.getElementById('bio-output');
            const generateBioBtn = document.getElementById('generate-bio-btn');
            const listenBtn = document.getElementById('listen-btn');
            let audioContext;

            // Helper function to handle exponential backoff for API calls
            const callApiWithBackoff = async (apiCall, maxRetries = 5, initialDelay = 1000) => {
                let retries = 0;
                let delay = initialDelay;
                while (retries < maxRetries) {
                    try {
                        const response = await apiCall();
                        if (response.status === 429) {
                            throw new Error('Too many requests, retrying with backoff.');
                        }
                        if (!response.ok) {
                            throw new Error(`API call failed with status: ${response.status}`);
                        }
                        return response;
                    } catch (error) {
                        console.warn(`Attempt ${retries + 1} failed: ${error.message}. Retrying in ${delay / 1000}s...`);
                        retries++;
                        if (retries < maxRetries) {
                            await new Promise(res => setTimeout(res, delay));
                            delay *= 2; // Exponential backoff
                        } else {
                            throw error;
                        }
                    }
                }
            };

            // Gemini Text Generation API call
            const generateBio = async () => {
                bioOutput.innerHTML = `<span class="loading-spinner"></span> জেনারেট হচ্ছে...`;
                generateBioBtn.disabled = true;
                listenBtn.style.display = 'none';

                const prompt = `Write a short, professional, and inspiring bio for a digital creator named Apurbo Islam (AP) who has a YouTube channel (@ap-takunation), a Facebook profile, a Facebook page, a TikTok account (@clone.ap), and an Instagram account (@ap_._sui). The bio should be in the Bangla language and should be around 50 words. Focus on themes of digital creation, connecting with an audience, and sharing passion.`;

                const payload = {
                    contents: [{
                        parts: [{
                            text: prompt
                        }]
                    }],
                    generationConfig: {
                        temperature: 0.7,
                        topP: 1,
                        topK: 1
                    }
                };

                const apiKey = "";
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${apiKey}`;

                try {
                    const response = await callApiWithBackoff(() => fetch(apiUrl, {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json'
                        },
                        body: JSON.stringify(payload)
                    }));
                    const result = await response.json();
                    
                    if (result.candidates && result.candidates.length > 0 &&
                        result.candidates[0].content && result.candidates[0].content.parts &&
                        result.candidates[0].content.parts.length > 0) {
                        const generatedText = result.candidates[0].content.parts[0].text;
                        bioOutput.textContent = generatedText;
                        listenBtn.style.display = 'block';
                    } else {
                        bioOutput.textContent = 'বায়ো জেনারেট করা সম্ভব হয়নি। আবার চেষ্টা করুন।';
                    }
                } catch (error) {
                    console.error("Failed to generate bio:", error);
                    bioOutput.textContent = 'বায়ো জেনারেট করার সময় একটি ত্রুটি হয়েছে।';
                } finally {
                    generateBioBtn.disabled = false;
                }
            };

            // Gemini TTS API call and audio playback
            const playAudio = async () => {
                const textToSpeak = bioOutput.textContent;
                if (!textToSpeak || textToSpeak.includes('জেনারেট') || textToSpeak.includes('ত্রুটি')) {
                    return;
                }

                listenBtn.disabled = true;
                listenBtn.innerHTML = 'লোড হচ্ছে...';

                const payload = {
                    contents: [{
                        parts: [{ text: textToSpeak }]
                    }],
                    generationConfig: {
                        responseModalities: ["AUDIO"],
                        speechConfig: {
                            voiceConfig: {
                                prebuiltVoiceConfig: { voiceName: "Iapetus" } // Using a clear, informative voice
                            }
                        }
                    },
                    model: "gemini-2.5-flash-preview-tts"
                };
                const apiKey = "";
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-tts:generateContent?key=${apiKey}`;
                
                let audioData = null;
                let sampleRate = 0;

                try {
                    const response = await callApiWithBackoff(() => fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    }));
                    const result = await response.json();
                    const part = result?.candidates?.[0]?.content?.parts?.[0];
                    if (part && part.inlineData && part.inlineData.data && part.inlineData.mimeType) {
                        audioData = part.inlineData.data;
                        const match = part.inlineData.mimeType.match(/rate=(\d+)/);
                        if (match && match[1]) {
                            sampleRate = parseInt(match[1], 10);
                        } else {
                            throw new Error('Could not parse audio sample rate.');
                        }
                    } else {
                        throw new Error('Unexpected API response structure.');
                    }

                    // Convert base64 to ArrayBuffer
                    const base64ToArrayBuffer = (base64) => {
                        const binaryString = atob(base64);
                        const len = binaryString.length;
                        const bytes = new Uint8Array(len);
                        for (let i = 0; i < len; i++) {
                            bytes[i] = binaryString.charCodeAt(i);
                        }
                        return bytes.buffer;
                    };
                    const pcmData = base64ToArrayBuffer(audioData);

                    // Convert PCM to WAV format
                    const pcmToWav = (pcm, sampleRate) => {
                        const buffer = new ArrayBuffer(44 + pcm.length * 2);
                        const view = new DataView(buffer);
                        
                        // RIFF identifier
                        writeString(view, 0, 'RIFF');
                        // file length
                        view.setUint32(4, 36 + pcm.length * 2, true);
                        // RIFF type
                        writeString(view, 8, 'WAVE');
                        // format chunk identifier
                        writeString(view, 12, 'fmt ');
                        // format chunk length
                        view.setUint32(16, 16, true);
                        // sample format (1 = PCM)
                        view.setUint16(20, 1, true);
                        // channel count
                        view.setUint16(22, 1, true);
                        // sample rate
                        view.setUint32(24, sampleRate, true);
                        // byte rate (sample rate * block align)
                        view.setUint32(28, sampleRate * 2, true);
                        // block align (channels * bytes per sample)
                        view.setUint16(32, 2, true);
                        // bits per sample
                        view.setUint16(34, 16, true);
                        // data chunk identifier
                        writeString(view, 36, 'data');
     

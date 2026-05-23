# Gameriyyyy
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Teman Bermain & Belajar</title>
    <style>
        /* Menggunakan font yang ramah anak dan warna latar belakang pastel */
        body {
            font-family: 'Comic Sans MS', 'Chalkboard SE', 'Casual', sans-serif;
            background: linear-gradient(135deg, #FFE5EC, #F0E6FF, #E8F0FE);
            min-height: 100vh;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #4A4A4A;
            overflow-x: hidden;
        }

        /* Wadah utama aplikasi */
        .container {
            background-color: rgba(255, 255, 255, 0.95);
            padding: 30px;
            border-radius: 24px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.05);
            text-align: center;
            max-width: 500px;
            width: 90%;
            border: 4px solid #FFF;
            position: relative;
        }

        /* Stiker-stiker imut di pojokan */
        .sticker {
            font-size: 2rem;
            position: absolute;
            animation: bounce 2s infinite alternate;
        }
        .sticker-1 { top: -20px; left: -20px; }
        .sticker-2 { bottom: -20px; right: -20px; }
        .sticker-3 { top: -25px; right: -20px; font-size: 2.5rem; }

        @keyframes bounce {
            0% { transform: translateY(0) rotate(-5deg); }
            100% { transform: translateY(-10px) rotate(5deg); }
        }

        h1 {
            color: #FF70A6;
            font-size: 1.8rem;
            margin-bottom: 10px;
        }

        p {
            font-size: 1.1rem;
            line-height: 1.5;
        }

        /* Gaya tombol pilihan */
        .btn-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 25px;
        }

        button {
            padding: 12px 28px;
            font-size: 1.1rem;
            font-family: inherit;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.2s ease;
            font-weight: bold;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .btn-oke {
            background-color: #A3E4D7;
            color: #2E4053;
        }
        .btn-oke:hover { background-color: #76D7C4; transform: scale(1.05); }

        .btn-tidak {
            background-color: #FADBD8;
            color: #78281F;
        }
        .btn-tidak:hover { background-color: #F5B7B1; transform: scale(1.05); }

        /* Menyembunyikan elemen secara default */
        .hidden {
            display: none !important;
        }

        /* Gaya untuk form input */
        .input-group {
            margin-top: 20px;
        }

        input[type="text"] {
            padding: 12px;
            width: 80%;
            border: 2px solid #D2B4DE;
            border-radius: 12px;
            font-size: 1rem;
            font-family: inherit;
            outline: none;
            text-align: center;
        }

        input[type="text"]:focus {
            border-color: #BB8FCE;
        }

        /* Gaya area kuis */
        .quiz-box {
            background-color: #E8F8F5;
            padding: 20px;
            border-radius: 16px;
            margin-top: 20px;
            border-left: 5px solid #76D7C4;
            text-align: left;
        }

        .quiz-options {
            list-style: none;
            padding: 0;
        }

        .quiz-options li {
            background: white;
            padding: 10px 15px;
            margin: 8px 0;
            border-radius: 8px;
            cursor: pointer;
            border: 1px solid #E0E0E0;
            transition: background 0.2s;
        }

        .quiz-options li:hover {
            background: #D4EFDF;
        }

        #feedback {
            margin-top: 15px;
            font-weight: bold;
            text-align: center;
        }

        /* Gaya untuk area hiburan (Video/Mukbang) */
        .video-container {
            margin-top: 20px;
        }
        .video-wrapper {
            position: relative;
            padding-bottom: 56.25%; /* Rasio 16:9 */
            height: 0;
            margin-bottom: 15px;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }
        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- Stiker Dekorasi Emote Imut -->
        <div class="sticker sticker-1">🧸</div>
        <div class="sticker sticker-2">🎨</div>
        <div class="sticker sticker-3">✨</div>

        <!-- HALAMAN UTAMA -->
        <div id="papan-utama">
            <h1>Halo Sahabat Pintar! 👋</h1>
            <p>Hari ini kita mau main apa nih? Apakah kamu mau bermain sambil belajar bersama aku?</p>
            <div class="btn-container">
                <button class="btn-oke" onclick="pilihOke()">Oke! 🚀</button>
                <button class="btn-tidak" onclick="pilihTidak()">Tidak 🐧</button>
            </div>
        </div>

        <!-- HALAMAN INPUT MATA PELAJARAN -->
        <div id="papan-input" class="hidden">
            <h1>Wah, Pilihan yang Bagus! 💡</h1>
            <p>Tuliskan mata pelajaran yang ingin kamu pelajari hari ini:</p>
            <div class="input-group">
                <input type="text" id="mapel-input" placeholder="Contoh: Matematika, IPA, Sejarah...">
                <div class="btn-container">
                    <button class="btn-oke" onclick="buatKuis()">Mulai Kuis! 🎯</button>
                </div>
            </div>
        </div>

        <!-- HALAMAN KUIS -->
        <div id="papan-kuis" class="hidden">
            <h1 id="kuis-judul">Kuis Seru</h1>
            <div class="quiz-box">
                <p id="pertanyaan">Pertanyaan akan muncul di sini...</p>
                <ul class="quiz-options" id="pilihan-jawaban">
                    <!-- Pilihan jawaban akan dibuat oleh JavaScript -->
                </ul>
            </div>
            <p id="feedback"></p>
            <div class="btn-container">
                <button class="btn-tidak" onclick="kembaliKeUtama()">Kembali Utama 🏡</button>
            </div>
        </div>

        <!-- HALAMAN HIBURAN (TIDAK) -->
        <div id="papan-hiburan" class="hidden">
            <h1>Waktunya Bersantai! 🍿</h1>
            <p>Tidak apa-apa, ayo kita tonton video lucu dan mukbang yang seru ini untuk menghibur harimu!</p>
            
            <div class="video-container">
                <!-- Video Lucu -->
                <div class="video-wrapper">
                    <iframe src="https://www.youtube.com/embed/31767SGYA7M" title="Video Hewan Lucu" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>
                <!-- Video Mukbang -->
                <div class="video-wrapper">
                    <iframe src="https://www.youtube.com/embed/5UfO_Yclj88" title="Mukbang Menghibur" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>
            </div>

            <div class="btn-container">
                <button class="btn-oke" onclick="kembaliKeUtama()">Aku Mau Belajar Sekarang 📚</button>
            </div>
        </div>
    </div>

    <script>
        // Mengambil elemen-elemen halaman
        const papanUtama = document.getElementById('papan-utama');
        const papanInput = document.getElementById('papan-input');
        const papanKuis = document.getElementById('papan-kuis');
        const papanHiburan = document.getElementById('papan-hiburan');

        // Bank data kuis sederhana buatan "Teman Belajar"
        const bankKuis = {
            "matematika": {
                tanya: "Jika kamu punya 5 apel lalu diberikan lagi oleh temanmu 3 apel, berapa total apelmu sekarang? 🍎",
                opsi: ["6 Apel", "7 Apel", "8 Apel", "9 Apel"],
                kunci: 2 // indeks ke-2 yaitu "8 Apel"
            },
            "ipa": {
                tanya: "Hewan apa yang dikenal sebagai Raja Hutan dan memiliki suara auman yang keras? 🦁",
                opsi: ["Kucing", "Singa", "Gajah", "Jerapah"],
                kunci: 1
            },
            "bahasa indonesia": {
                tanya: "Lawan kata dari kata 'Besar' adalah... 🐜",
                opsi: ["Tinggi", "Panjang", "Kecil", "Lebar"],
                kunci: 2
            },
            "default": {
                tanya: "Wah, mata pelajaran yang kamu pilih sangat unik! Kamu siap untuk terus belajar hal baru setiap hari?",
                opsi: ["Siap Banget! 🌟", "Tentu Saja! 🚀"],
                kunci: 0
            }
        };

        function pilihOke() {
            papanUtama.classList.add('hidden');
            papanInput.classList.remove('hidden');
        }

        function pilihTidak() {
            papanUtama.classList.add('hidden');
            papanHiburan.classList.remove('hidden');
        }

        function buatKuis() {
            const inputUser = document.getElementById('mapel-input').value.trim().toLowerCase();
            
            if (inputUser === "") {
                alert("Tuliskan dulu mata pelajarannya yaa! 😉");
                return;
            }

            papanInput.classList.add('hidden');
            papanKuis.classList.remove('hidden');

            // Menampilkan judul mata pelajaran yang diketik user
            document.getElementById('kuis-judul').innerText = `Kuis: ${inputUser.toUpperCase()} 📝`;
            
            // Cek apakah ada di bank data, jika tidak pakai kuis default
            const dataKuis = bankKuis[inputUser] || bankKuis["default"];
            
            document.getElementById('pertanyaan').innerText = dataKuis.tanya;
            
            // Mengosongkan feedback dan pilihan sebelumnya
            document.getElementById('feedback').innerText = "";
            const listOpsi = document.getElementById('pilihan-jawaban');
            listOpsi.innerHTML = "";

            // Membuat list opsi jawaban secara dinamis
            dataKuis.opsi.forEach((opsiText, index) => {
                const li = document.createElement('li');
                li.innerText = opsiText;
                li.onclick = function() {
                    cekJawaban(index, dataKuis.kunci);
                };
                listOpsi.appendChild(li);
            });
        }

        function cekJawaban(dipilih, kunci) {
            const feedback = document.getElementById('feedback');
            if (dipilih === kunci) {
                feedback.innerText = "🎉 Hebat! Jawabanmu Benar! Kamu pintar sekali! 🌟";
                feedback.style.color = "#27AE60";
            } else {
                feedback.innerText = "🎯 Hampir tepat! Ayo coba diingat-ingat lagi yuk! 💪";
                feedback.style.color = "#E74C3C";
            }
        }

        function kembaliKeUtama() {
            // Reset semua inputan
            document.getElementById('mapel-input').value = "";
            
            // Sembunyikan semua halaman tambahan, tampilkan halaman utama
            papanInput.classList.add('hidden');
            papanKuis.classList.add('hidden');
            papanHiburan.classList.add('hidden');
            papanUtama.classList.remove('hidden');
        }
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BÀI THU HOẠCH CUỐI KÌ 2 - Nguyễn Anh Minh</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;800&display=swap" rel="stylesheet">
    <style>
        :root { 
            --primary: #1e3a8a; 
            --secondary: #3b82f6; 
            --accent: #60a5fa;
            --bg-dark: #020617;
        }

        html, body { 
            margin: 0; padding: 0;
            background-color: var(--bg-dark);
            color: #f1f5f9;
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
            /* cursor: none; -> Đã loại bỏ để dùng chuột mặc định */
        }

        /* BACKGROUND ANIMATION */
        .bg-glow {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle at 50% 50%, #1e3a8a 0%, #020617 100%);
            z-index: -2;
        }
        .stars {
            position: fixed; width: 100%; height: 100%; z-index: -1;
            background: url('https://www.transparenttextures.com/patterns/stardust.png');
            opacity: 0.4;
        }

        /* INTRO SCREEN */
        #video-intro {
            position: fixed; inset: 0; z-index: 10000;
            background: #000; display: flex; align-items: center; justify-content: center;
            transition: all 1.2s cubic-bezier(0.85, 0, 0.15, 1);
        }
        .btn-enter {
            padding: 1.5rem 5rem;
            background: linear-gradient(45deg, #1e3a8a, #3b82f6);
            color: white; border-radius: 99px;
            font-weight: 800; letter-spacing: 0.5em;
            cursor: pointer; border: none;
            transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-transform: uppercase;
            box-shadow: 0 0 50px rgba(59, 130, 246, 0.4);
        }
        .btn-enter:hover {
            transform: scale(1.1) translateY(-5px);
            box-shadow: 0 20px 60px rgba(59, 130, 246, 0.6);
            letter-spacing: 0.7em;
        }

        /* MAIN CONTENT */
        #main-content {
            opacity: 0; display: none;
            transition: opacity 2s ease;
        }

        .glass-card {
            background: rgba(255, 255, 255, 0.02);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 3rem;
            margin-bottom: 8rem;
            transition: all 0.5s ease;
        }
        .glass-card:hover {
            background: rgba(255, 255, 255, 0.05);
            border-color: rgba(59, 130, 246, 0.3);
        }

        .title-underline::after { 
            content: ''; display: block; width: 120px; height: 6px; 
            background: linear-gradient(to right, #3b82f6, transparent); 
            margin-top: 20px; border-radius: 10px; 
        }

        .image-container { 
            border-radius: 2.5rem; overflow: hidden; 
            border: 1px solid rgba(255,255,255,0.1);
            position: relative;
        }
        .image-container img { transition: transform 1.5s cubic-bezier(0.19, 1, 0.22, 1); }
        .image-container:hover img { transform: scale(1.15); }

        .career-tag {
            background: rgba(59, 130, 246, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.05);
            padding: 2.5rem; border-radius: 2rem;
            transition: all 0.4s;
        }
        .career-tag:hover {
            background: rgba(59, 130, 246, 0.15);
            transform: translateY(-5px);
            border-color: var(--secondary);
        }

        .step-num {
            width: 60px; height: 60px;
            background: linear-gradient(135deg, #1e3a8a, #3b82f6);
            border-radius: 20px; display: flex;
            align-items: center; justify-content: center;
            font-weight: 900; font-size: 1.5rem;
            box-shadow: 0 10px 20px rgba(30, 58, 138, 0.5);
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
        .floating { animation: float 6s ease-in-out infinite; }

        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: var(--bg-dark); }
        ::-webkit-scrollbar-thumb { background: #1e3a8a; border-radius: 10px; }
    </style>
</head>
<body>

    <div class="bg-glow"></div>
    <div class="stars"></div>

    <!-- Màn hình chào -->
    <div id="video-intro">
        <div class="text-center px-6">
            <div class="floating">
                <h2 class="text-6xl md:text-8xl font-black mb-6 tracking-tighter text-white uppercase italic">Sonadezi</h2>
                <p class="text-blue-400 tracking-[0.8em] font-bold text-xs mb-12 opacity-80 uppercase">The Future Journey • 2024</p>
            </div>
            <button class="btn-enter" onclick="unlockContent()">Khởi động hành trình</button>
        </div>
    </div>

    <!-- Nội dung chính -->
    <div id="main-content">
        <header class="pt-48 pb-32 px-6 text-center">
            <div data-aos="zoom-in">
                <span class="px-6 py-2 bg-blue-500/20 rounded-full text-blue-400 font-black text-[10px] tracking-widest uppercase mb-8 border border-blue-400/30 inline-block">Trải nghiệm thực tế</span>
                <h1 class="text-7xl md:text-9xl font-black mb-8 uppercase italic leading-none">
                    Bài Thu Hoạch<br><span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-white">Kỳ II</span>
                </h1>
                <p class="text-2xl tracking-[0.4em] font-light text-slate-400 mt-10 uppercase">NGUYỄN ANH MINH • LỚP 9/2-22</p>
            </div>
        </header>

        <main class="max-w-6xl mx-auto px-6">

            <!-- CÂU 1 -->
            <section class="glass-card p-12 md:p-24" data-aos="fade-up">
                <h2 class="text-4xl font-black text-white mb-14 uppercase title-underline italic">1. Dấu ấn khó quên tại Sonadezi</h2>
                <div class="grid lg:grid-cols-2 gap-20 items-center">
                    <div class="text-slate-300 text-xl leading-relaxed text-justify space-y-8 font-light">
                        <p>Điều đầu tiên chạm vào cảm xúc của em khi đặt chân tới <span class="text-blue-400 font-black">Cao đẳng Sonadezi</span> chính là sự hòa quyện hoàn hảo giữa công nghệ hiện đại và thiên nhiên xanh mát. Không gian tại đây không gợi lên sự khô khan của những xưởng máy, mà mang tinh thần của một học viện đẳng cấp quốc tế.</p>
                        <p>Em đặc biệt ấn tượng với sự nhiệt huyết của các anh chị sinh viên tại khu vực <span class="text-blue-400 font-bold uppercase italic">Bóng bàn</span>. Đó không chỉ là giải trí, mà là hình ảnh minh chứng cho một lối sống năng động, khỏe mạnh của thế hệ trẻ. Sự chuyên nghiệp trong từng khu xưởng thực hành cho em thấy rằng: Để thành công, người học cần một môi trường tôn trọng sự sáng tạo và trải nghiệm thực tế hơn là những trang giáo trình dày đặc.</p>
                    </div>
                    <div class="image-container shadow-[0_50px_100px_rgba(0,0,0,0.5)]">
                        <img src="https://i.postimg.cc/cJhtNtk6/z7741929847974-565a16d5f9aa9c7c38178f18723002e7.jpg" alt="[Không gian trường Sonadezi]" class="w-full">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
                    </div>
                </div>
            </section>

            <!-- CÂU 2 -->
            <section class="glass-card p-12 md:p-24" data-aos="fade-up">
                <h2 class="text-4xl font-black text-white mb-16 uppercase title-underline italic">2. Phân tích nhóm ngành nghề tiềm năng</h2>
                <div class="grid md:grid-cols-2 gap-10">
                    <div class="career-tag">
                        <div class="text-blue-400 text-5xl mb-6 font-black opacity-20">01</div>
                        <h3 class="text-white font-black text-2xl mb-6 uppercase tracking-tight">Công nghệ Điện Công Nghiệp</h3>
                        <p class="text-slate-400 text-base leading-relaxed text-justify">Đây là "trái tim" của mọi nhà máy. Em đã thấy được các hệ thống điều khiển phức tạp, đòi hỏi người kỹ sư không chỉ có đôi tay khéo léo mà còn cần tư duy logic sắc bén để xử lý các mạch điện hàng nghìn volt. Trong kỷ nguyên tự động hóa, đây là ngành nắm giữ tương lai của sản xuất.</p>
                    </div>
                    <div class="career-tag">
                        <div class="text-blue-400 text-5xl mb-6 font-black opacity-20">02</div>
                        <h3 class="text-white font-black text-2xl mb-6 uppercase tracking-tight">Nghệ thuật Bartender</h3>
                        <p class="text-slate-400 text-base leading-relaxed text-justify">Hơn cả một người pha chế, đây là những "nghệ sĩ" của vị giác. Em được tìm hiểu về sự tinh tế trong việc phối trộn hương vị, màu sắc và kỹ năng giao tiếp tâm lý khách hàng. Một Bartender chuyên nghiệp cần sự kiên nhẫn và khả năng trình diễn lôi cuốn.</p>
                    </div>
                    <div class="career-tag">
                        <div class="text-blue-400 text-5xl mb-6 font-black opacity-20">03</div>
                        <h3 class="text-white font-black text-2xl mb-6 uppercase tracking-tight">Quản trị Khách sạn 5 Sao</h3>
                        <p class="text-slate-400 text-base leading-relaxed text-justify">Sự chỉn chu đến từng milimet tại khu mô phỏng khách sạn làm em choáng ngợp. Ngành này đòi hỏi quy chuẩn khắt khe về thái độ, ngoại ngữ và kỹ năng quản trị dịch vụ cao cấp. Đây chính là mảnh đất cho những người ưa thích sự lịch lãm và phục vụ khách hàng tận tâm.</p>
                    </div>
                    <div class="career-tag">
                        <div class="text-blue-400 text-5xl mb-6 font-black opacity-20">04</div>
                        <h3 class="text-white font-black text-2xl mb-6 uppercase tracking-tight">Truyền thông Đa phương tiện</h3>
                        <p class="text-slate-400 text-base leading-relaxed text-justify">Sáng tạo không biên giới là từ khóa cho ngành này. Em hiểu rằng đằng sau mỗi chiến dịch truyền thông thành công là sự phối hợp của tư duy hình ảnh, công nghệ phần mềm và nắm bắt tâm lý cộng đồng. Đây là ngành nghề đòi hỏi sự thay đổi liên tục để không bị tụt hậu.</p>
                    </div>
                </div>
            </section>

            <!-- CÂU 3 -->
            <section class="glass-card p-12 md:p-24" data-aos="fade-up">
                <h2 class="text-4xl font-black text-white mb-16 uppercase title-underline italic">3. Nguồn cảm hứng bất tận từ thực tế</h2>
                
                <div class="space-y-20">
                    <div class="bg-gradient-to-br from-blue-900/40 to-blue-600/10 p-12 rounded-[3rem] border border-blue-400/20 relative overflow-hidden group">
                        <div class="absolute top-0 right-0 p-10 opacity-10 group-hover:opacity-20 transition-opacity">
                            <svg width="100" height="100" viewBox="0 0 24 24" fill="currentColor" class="text-white"><path d="M14.017 21L14.017 18C14.017 16.8954 14.9124 16 16.017 16H19.017C19.5693 16 20.017 15.5523 20.017 15V9C20.017 8.44772 19.5693 8 19.017 8H15.017C14.4647 8 14.017 8.44772 14.017 9V12C14.017 12.5523 13.5693 13 13.017 13H11.017C10.4647 13 10.017 12.5523 10.017 12V9C10.017 7.34315 11.3601 6 13.017 6H19.017C20.6739 6 22.017 7.34315 22.017 9V15C22.017 18.3137 19.3307 21 16.017 21H14.017ZM3.017 21L3.017 18C3.017 16.8954 3.91243 16 5.017 16H8.017C8.56928 16 9.017 15.5523 9.017 15V9C9.017 8.44772 8.56928 8 8.017 8H4.017C3.46472 8 3.017 8.44772 3.017 9V12C3.017 12.5523 2.56928 13 2.017 13H0.017C-0.535282 13 -1.017 12.5523 -1.017 12V9C-1.017 7.34315 0.326142 6 2.017 6H8.017C9.67386 6 11.017 7.34315 11.017 9V15C11.017 18.3137 8.33071 21 5.017 21H3.017Z"/></svg>
                        </div>
                        <p class="text-3xl md:text-5xl italic font-light text-blue-100 leading-tight text-center relative z-10">
                            "Lý thuyết chỉ là những con chữ nằm yên trên mặt giấy, nhưng tại <span class="text-white font-black">Sonadezi</span>, em thấy kiến thức đang sống, đang vận động và trực tiếp tạo ra giá trị cho xã hội."
                        </p>
                    </div>

                    <div class="grid lg:grid-cols-2 gap-16 items-start">
                        <div class="space-y-10">
                            <div class="p-8 border-l-4 border-blue-500 bg-white/5 rounded-r-3xl">
                                <h3 class="text-2xl font-bold text-white mb-4 uppercase">Sức mạnh của sự trải nghiệm</h3>
                                <p class="text-slate-400 leading-relaxed text-lg italic text-justify">
                                    Chuyến đi đã thay đổi hoàn toàn tư duy của em về việc chọn nghề. Thay vì mơ mộng về những hào nhoáng xa vời, em học được cách trân trọng những giá trị cốt lõi: sự tỉ mỉ của người thợ điện, sự tinh tế của người Bartender hay sự nhạy bén của chuyên viên truyền thông. Cảm hứng lớn nhất chính là nhìn thấy niềm say mê trong mắt những người đang làm công việc của họ một cách chuyên nghiệp nhất.
                                </p>
                            </div>
                            <div class="p-8 border-l-4 border-blue-400 bg-white/5 rounded-r-3xl">
                                <h3 class="text-2xl font-bold text-white mb-4 uppercase">Tương lai trong tầm tay</h3>
                                <p class="text-slate-400 leading-relaxed text-lg italic text-justify">
                                    Em nhận ra rằng mỗi ngành nghề đều có vẻ đẹp riêng nếu chúng ta đủ tâm huyết. Sonadezi không chỉ dạy nghề, mà còn dạy cách để trở thành một con người có kỷ luật và đạo đức nghề nghiệp. Điều này thôi thúc em phải cố gắng hơn nữa để một ngày nào đó cũng có thể tự tin làm chủ công nghệ và tương lai của chính mình.
                                </p>
                            </div>
                        </div>

                        <div class="grid grid-cols-1 gap-8">
                            <div class="image-container group h-[400px]">
                                <img src="https://i.postimg.cc/jSwDLdqn/z7741929871590-7b9e3050dc85509d1d42f7f3d84acc54.jpg" class="w-full h-full object-cover">
                                <div class="absolute inset-0 bg-blue-600/40 opacity-0 group-hover:opacity-100 transition-all flex flex-col justify-end p-10">
                                    <h4 class="text-white font-black text-3xl uppercase transform translate-y-10 group-hover:translate-y-0 transition-transform">Lao động sáng tạo</h4>
                                    <p class="text-blue-100 mt-2 opacity-0 group-hover:opacity-100 transition-delay-300">Nơi những giấc mơ bắt đầu được hiện thực hóa bằng đôi tay khéo léo.</p>
                                </div>
                            </div>
                            <div class="image-container group h-[400px]">
                                <img src="https://i.postimg.cc/3Jw4QFP4/z7741929859003-ba9fd25de60a98782baf10ab0dc0c4a7.jpg" class="w-full h-full object-cover">
                                <div class="absolute inset-0 bg-indigo-600/40 opacity-0 group-hover:opacity-100 transition-all flex flex-col justify-end p-10">
                                    <h4 class="text-white font-black text-3xl uppercase transform translate-y-10 group-hover:translate-y-0 transition-transform">Kỷ nguyên số</h4>
                                    <p class="text-indigo-100 mt-2 opacity-0 group-hover:opacity-100 transition-delay-300">Công nghệ không thay thế con người, nó làm con người trở nên vĩ đại hơn.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- CÂU 4 -->
            <section class="glass-card p-12 md:p-24" data-aos="fade-up">
                <h2 class="text-4xl font-black text-white mb-20 uppercase title-underline italic">4. Chiến lược Kế hoạch Hành động</h2>
                <div class="relative space-y-16">
                    <div class="absolute left-[30px] top-0 w-1 h-full bg-blue-900/30 -z-10 hidden md:block"></div>
                    
                    <div class="flex flex-col md:flex-row gap-10 items-start group">
                        <div class="step-num group-hover:scale-110 transition-transform">01</div>
                        <div class="bg-white/5 p-10 rounded-3xl border border-white/5 flex-1">
                            <h4 class="text-blue-400 font-black text-xl mb-4 uppercase">Giai đoạn Chinh phục (Hiện tại - 6 tháng)</h4>
                            <p class="text-slate-300 leading-relaxed text-lg text-justify">Tập trung toàn lực vào kỳ thi tuyển sinh lớp 10. Em sẽ xây dựng lộ trình học tập kỷ luật, đặc biệt ưu tiên các môn tư duy như Toán và Tiếng Anh để tạo nền tảng vững chắc nhất cho việc học nghề cao cấp sau này.</p>
                        </div>
                    </div>

                    <div class="flex flex-col md:flex-row gap-10 items-start group">
                        <div class="step-num group-hover:scale-110 transition-transform">02</div>
                        <div class="bg-white/5 p-10 rounded-3xl border border-white/5 flex-1">
                            <h4 class="text-blue-400 font-black text-xl mb-4 uppercase">Giai đoạn Mở rộng (Cấp THPT)</h4>
                            <p class="text-slate-300 leading-relaxed text-lg text-justify">Bên cạnh việc học văn hóa, em sẽ tham gia các khóa học online ngắn hạn về kỹ năng mềm, tư duy sáng tạo và đặc biệt là công nghệ số để bắt nhịp với sự thay đổi của các ngành nghề truyền thông và quản trị khách sạn.</p>
                        </div>
                    </div>

                    <div class="flex flex-col md:flex-row gap-10 items-start group">
                        <div class="step-num group-hover:scale-110 transition-transform">03</div>
                        <div class="bg-white/5 p-10 rounded-3xl border border-white/5 flex-1">
                            <h4 class="text-blue-400 font-black text-xl mb-4 uppercase">Giai đoạn Định hình (Sau THPT)</h4>
                            <p class="text-slate-300 leading-relaxed text-lg text-justify">Cân nhắc lựa chọn môi trường thực học - thực hành như Sonadezi để phát triển chuyên môn sâu. Em sẽ tìm kiếm các cơ hội thực tập sớm tại các doanh nghiệp để tích lũy kinh nghiệm thực tiễn ngay khi còn là sinh viên.</p>
                        </div>
                    </div>

                    <div class="flex flex-col md:flex-row gap-10 items-start group">
                        <div class="step-num group-hover:scale-110 transition-transform">04</div>
                        <div class="bg-white/5 p-10 rounded-3xl border border-white/5 flex-1">
                            <h4 class="text-blue-400 font-black text-xl mb-4 uppercase">Giai đoạn Về đích (Dài hạn)</h4>
                            <p class="text-slate-300 leading-relaxed text-lg text-justify">Trở thành một chuyên gia có tâm và có tầm trong lĩnh vực đã chọn. Không ngừng học hỏi, rèn luyện thói quen kỷ luật tự giác và luôn giữ vững tinh thần "Học để sáng tạo - Học để kiến tạo giá trị".</p>
                        </div>
                    </div>
                </div>
            </section>

        </main>

        <footer class="py-32 text-center border-t border-white/10 relative overflow-hidden">
            <div class="absolute inset-0 bg-blue-900/10 blur-[150px] -z-10"></div>
            <p class="text-blue-400 font-black tracking-[1em] uppercase mb-6 text-sm">Nguyễn Anh Minh</p>
            <p class="text-xs text-slate-500 tracking-[0.5em] uppercase opacity-40">Digital Harvest Portfolio • Sonadezi Experience • 2024</p>
        </footer>
    </div>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        function unlockContent() {
            const intro = document.getElementById('video-intro');
            const main = document.getElementById('main-content');
            
            // Effect: Intro screen fades out and zooms in
            intro.style.opacity = '0';
            intro.style.transform = 'scale(1.2)';
            
            setTimeout(() => {
                intro.style.display = 'none';
                main.style.display = 'block';
                
                // Allow a small delay for browser to register display:block before fading in
                setTimeout(() => {
                    main.style.opacity = '1';
                    AOS.init({ 
                        duration: 1200, 
                        once: true,
                        offset: 100 
                    });
                }, 50);
            }, 1200);
        }

        // Standard security - prevent right click
        document.addEventListener('contextmenu', e => e.preventDefault());
        document.onkeydown = function(e) {
            if(e.keyCode == 123 || (e.ctrlKey && e.shiftKey && e.keyCode == 73)) return false;
        };
    </script>
</body>
</html>

<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Altum Telecom - Servicios de Redes y Seguridad</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Altum Corporate (Blue: #0056D2, Green: #00A86B, Neutrals: White/Light Gray) -->
    <!-- Application Structure Plan: A single-page, vertical-scrolling SPA with thematic sections. The core is an interactive service explorer where users filter between 'Networking' and 'Security' categories using buttons. This structure simplifies decision-making by presenting comparable packages side-by-side, which is more user-friendly than a static, linear list. The flow guides the user from a general introduction to specific package details, value-added services, and finally a clear call to action. -->
    <!-- Visualization & Content Choices: Report Info: Service packages -> Goal: Inform & Compare -> Presentation Method: Interactive card-based layout with button filters -> Interaction: JS toggles visibility of cards based on 'data-category' attribute. Report Info: Service features -> Goal: Clarify -> Presentation Method: Unicode icons (e.g., 🏠, 🚀, 🔒) and bulleted lists (ul/li) -> Interaction: Hover effects on cards for visual feedback. This approach avoids complex libraries like Chart.js, which are unnecessary for this content, and adheres to the NO SVG/Mermaid rule by using universally supported icons and structured HTML. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Poppins', sans-serif;
        }
        .altum-blue { background-color: #0d47a1; } /* Darker blue for better contrast */
        .altum-blue-text { color: #0d47a1; }
        .altum-green { background-color: #00A86B; }
        .altum-green-text { color: #00A86B; }
        .hero-bg {
            background-color: #f0f4f8;
            background-image: linear-gradient(to right, rgba(255, 255, 255, 0.95), rgba(255, 255, 255, 0.8)), url('https://placehold.co/1920x1080/e0e0e0/e0e0e0?text=+');
            background-size: cover;
            background-position: center;
        }
        .service-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .service-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }
        .filter-btn {
            transition: background-color 0.3s ease, color 0.3s ease;
        }
        .filter-btn.active {
            background-color: #0d47a1;
            color: white;
        }
        .premium-card {
            border-color: #00a86b !important;
            box-shadow: 0 0 20px rgba(0,168,107,0.4) !important;
            animation: pulse 2s infinite;
        }
        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.02);
            }
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-800">

    <header class="bg-white shadow-md sticky top-0 z-50">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <div class="w-12 h-12 rounded-full altum-blue flex items-center justify-center">
                    <span class="text-white text-2xl font-bold">A</span>
                </div>
                <span class="text-xl font-bold altum-blue-text">Altum Telecom</span>
            </div>
            <a href="#contact" id="contact-btn" class="altum-blue text-white font-semibold py-2 px-6 rounded-full hover:bg-blue-900 transition duration-300">Contáctanos</a>
        </nav>
    </header>

    <main>
        <section class="hero-bg py-20 md:py-32">
            <div class="container mx-auto px-6 text-center">
                <h1 class="text-4xl md:text-6xl font-bold altum-blue-text mb-4 leading-tight">Tu Conexión al Futuro, Sin Límites</h1>
                <p class="text-lg md:text-xl text-gray-600 max-w-3xl mx-auto mb-8">Soluciones expertas en redes domésticas y seguridad para mantener tu hogar conectado y protegido. Rápido, confiable y a tu medida.</p>
                <a href="#services" class="bg-green-500 text-white font-bold py-3 px-8 rounded-full text-lg hover:bg-green-600 transition duration-300">Explorar Servicios</a>
            </div>
        </section>

        <section id="our-promise" class="py-16 bg-blue-50 text-center">
            <div class="container mx-auto px-6">
                <h2 class="text-3xl font-bold altum-blue-text mb-4">Nuestra Promesa</h2>
                <p class="text-gray-600 max-w-2xl mx-auto">En Altum Telecom, somos más que instaladores; somos tus socios tecnológicos. Te ofrecemos soluciones personalizadas para tu hogar o negocio, garantizando calidad, soporte y una experiencia sin preocupaciones de principio a fin.</p>
            </div>
        </section>

        <section id="services" class="py-20">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold altum-blue-text">Nuestros Paquetes de Servicios</h2>
                    <p class="text-gray-600 mt-2">Selecciona una categoría para ver los paquetes diseñados para ti.</p>
                </div>

                <div class="flex justify-center space-x-2 md:space-x-4 mb-12">
                    <button class="filter-btn active py-2 px-6 rounded-full border-2 border-blue-800 text-blue-800 font-semibold" data-filter="all">Todos</button>
                    <button class="filter-btn py-2 px-6 rounded-full border-2 border-blue-800 text-blue-800 font-semibold" data-filter="networking">Redes Domésticas</button>
                    <button class="filter-btn py-2 px-6 rounded-full border-2 border-blue-800 text-blue-800 font-semibold" data-filter="security">Seguridad</button>
                </div>

                <div id="service-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    
                    <div class="service-card bg-white p-8 rounded-xl shadow-lg border-t-4 border-blue-500" data-category="networking" data-service="Conexión Total Hogar">
                        <div class="text-5xl mb-4 text-center">🏠</div>
                        <h3 class="text-2xl font-bold mb-4">Conexión Total Hogar</h3>
                        <ul class="space-y-3 text-gray-600">
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Instalación de router Wi-Fi</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Optimización de señal en toda la casa</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Conexión de dispositivos inteligentes</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Soporte remoto inicial (30 días)</li>
                        </ul>
                         <button class="request-service-btn altum-blue text-white w-full py-2 rounded-full mt-4 hover:bg-blue-900 transition">Solicitar</button>
                    </div>

                    <div class="service-card bg-white p-8 rounded-xl shadow-lg border-t-4 border-blue-700" data-category="networking" data-service="Hogar Inteligente Plus">
                        <div class="text-5xl mb-4 text-center">🚀</div>
                        <h3 class="text-2xl font-bold mb-4">Hogar Inteligente Plus</h3>
                        <ul class="space-y-3 text-gray-600">
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Todo lo del paquete básico</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Cableado estructurado (hasta 3 puntos)</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Instalación de Access Point o Wi-Fi Mesh</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Red de invitados y seguridad básica</li>
                        </ul>
                         <button class="request-service-btn altum-blue text-white w-full py-2 rounded-full mt-4 hover:bg-blue-900 transition">Solicitar</button>
                    </div>
                    
                    <div class="service-card bg-white p-8 rounded-xl shadow-lg border-t-4 border-blue-900" data-category="networking" data-service="Hogar Smart Avanzado">
                        <div class="text-5xl mb-4 text-center">🏡</div>
                        <h3 class="text-2xl font-bold mb-4">Hogar Smart Avanzado</h3>
                        <ul class="space-y-3 text-gray-600">
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Instalación de enchufes y bombillos inteligentes</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Cerraduras y timbres inteligentes</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Instalación de asistentes virtuales</li>
                        </ul>
                         <button class="request-service-btn altum-blue text-white w-full py-2 rounded-full mt-4 hover:bg-blue-900 transition">Solicitar</button>
                    </div>

                    <div class="service-card bg-white p-8 rounded-xl shadow-lg border-t-4 border-green-500" data-category="security" data-service="Protección Segura">
                        <div class="text-5xl mb-4 text-center">🔒</div>
                        <h3 class="text-2xl font-bold mb-4">Protección Segura (CCTV Básico)</h3>
                        <ul class="space-y-3 text-gray-600">
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Instalación de hasta 4 cámaras</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Configuración de DVR/NVR</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Visualización en celular y PC</li>
                            <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Grabación continua 24/7</li>
                        </ul>
                        <button class="request-service-btn altum-blue text-white w-full py-2 rounded-full mt-4 hover:bg-blue-900 transition">Solicitar</button>
                    </div>

                    <div class="service-card premium-card bg-white p-8 rounded-xl shadow-lg border-t-4 border-green-700" data-category="security" data-service="Protección Premium">
                        <div class="text-5xl mb-4 text-center">💎</div>
                        <h3 class="text-2xl font-bold mb-4">Protección Premium (CCTV Avanzado)</h3>
                        <ul class="space-y-3 text-gray-600">
                             <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Cámaras Full HD/IP con PoE</li>
                             <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Almacenamiento en disco duro + nube</li>
                             <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Optimización de red para cámaras</li>
                             <li class="flex items-center"><span class="altum-green-text mr-2">✔</span> Capacitación al cliente</li>
                        </ul>
                         <button class="request-service-btn altum-blue text-white w-full py-2 rounded-full mt-4 hover:bg-blue-900 transition">Solicitar</button>
                    </div>

                    <div class="service-card bg-white p-8 rounded-xl shadow-lg border-t-4 border-gray-500 md:col-span-2 lg:col-span-3" data-category="all" data-service="Servicios Adicionales">
                        <div class="text-5xl mb-4 text-center">💡</div>
                        <h3 class="text-2xl font-bold mb-4">Servicios Adicionales</h3>
                         <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-gray-600">
                            <p><strong>Mantenimiento Preventivo Anual:</strong> Revisión y limpieza de equipos.</p>
                            <p><strong>Soporte Técnico VIP:</strong> Solución de problemas en menos de 24 horas.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="detalles" class="py-20 bg-blue-50">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold altum-blue-text">Beneficios del Hogar Inteligente</h2>
                    <p class="text-gray-600 mt-2">Descubre cómo las automatizaciones pueden transformar tu espacio.</p>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div class="bg-white p-6 rounded-xl shadow-lg">
                        <div class="flex items-center space-x-4 mb-2">
                            <span class="text-4xl altum-green-text">💡</span>
                            <h4 class="text-xl font-semibold">Iluminación Inteligente</h4>
                        </div>
                        <p class="text-gray-600">Controla las luces de tu hogar de forma remota, programa horarios o ajústalas con comandos de voz para crear el ambiente perfecto.</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-lg">
                        <div class="flex items-center space-x-4 mb-2">
                            <span class="text-4xl altum-green-text">🌡️</span>
                            <h4 class="text-xl font-semibold">Climatización Automática</h4>
                        </div>
                        <p class="text-gray-600">Ahorra energía con termostatos inteligentes que se ajustan según tu presencia y temperatura exterior. Mantén siempre el confort en casa.</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-lg">
                        <div class="flex items-center space-x-4 mb-2">
                            <span class="text-4xl altum-green-text">🛡️</span>
                            <h4 class="text-xl font-semibold">Monitoreo y Seguridad</h4>
                        </div>
                        <p class="text-gray-600">Recibe alertas en tu celular si hay actividad inusual. Con las cámaras inteligentes, siempre tendrás tu hogar a la vista, estés donde estés.</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="contact" class="altum-blue text-white py-20">
            <div class="container mx-auto px-6 text-center">
                <h2 class="text-3xl md:text-4xl font-bold">¿Listo para mejorar tu conexión y seguridad?</h2>
                <p class="text-lg mt-2 mb-8">Contáctanos hoy para una evaluación gratuita y sin compromiso.</p>
                <a href="https://wa.me/18499939393" id="whatsapp-link" target="_blank" class="inline-block bg-white text-blue-800 font-bold text-2xl py-4 px-8 rounded-lg hover:bg-gray-100 transition duration-300">
                    📲 WhatsApp: +1 849-993-9393
                </a>
                 <p class="mt-4 text-gray-300">📍 Servicio en Santo Domingo</p>
            </div>
        </section>
    </main>
    
    <footer class="bg-gray-800 text-white py-6">
        <div class="container mx-auto px-6 text-center">
            <p>&copy; 2025 Altum Telecom. Todos los derechos reservados.</p>
        </div>
    </footer>
    
    <script>
        const filterButtons = document.querySelectorAll('.filter-btn');
        const serviceCards = document.querySelectorAll('.service-card');
        const whatsappLink = document.getElementById('whatsapp-link');
        const requestServiceButtons = document.querySelectorAll('.request-service-btn');
        
        filterButtons.forEach(button => {
            button.addEventListener('click', () => {
                const filter = button.dataset.filter;
                filterButtons.forEach(btn => btn.classList.remove('active'));
                button.classList.add('active');
                serviceCards.forEach(card => {
                    const cardCategory = card.dataset.category;
                    if (filter === 'all' || cardCategory === filter) {
                        card.style.display = 'block';
                    } else {
                        card.style.display = 'none';
                    }
                });
            });
        });

        requestServiceButtons.forEach(button => {
            button.addEventListener('click', (event) => {
                event.stopPropagation(); // Previene que el clic se propague a la tarjeta
                const serviceName = button.closest('.service-card').getAttribute('data-service');
                const whatsappMessage = `Hola, me interesa el paquete de ${serviceName}. ¿Podrías darme más información?`;
                const encodedMessage = encodeURIComponent(whatsappMessage);
                whatsappLink.href = `https://wa.me/18499939393?text=${encodedMessage}`;
                
                // Abre el enlace de WhatsApp directamente
                window.open(whatsappLink.href, '_blank');
            });
        });

    </script>
</body>
</html>

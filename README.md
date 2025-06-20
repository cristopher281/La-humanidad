<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Estudio científico sobre la evolución humana, teorías, hitos y etapas clave.">
  <title>Evolución Humana - Universidad Martin Lutero</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datalabels@2.0.0"></script>
  <style>
    /* ===== ESTILOS GLOBALES ===== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    :root {
      --color-primary: #1a472a;
      --color-secondary: #2c5d48;
      --color-accent: #d4af37;
      --color-light: #f5f5dc;
      --color-dark: #121e17;
      --color-text: #333;
      --color-text-light: #777;
      --transition: all 0.4s ease;
      --shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
      --shadow-hover: 0 8px 25px rgba(0, 0, 0, 0.1);
      --radius: 10px;
    }

    body {
      background: linear-gradient(135deg, #0c2b1d, #1a472a);
      color: white;
      min-height: 100vh;
      position: relative;
      overflow-x: hidden;
    }

    /* ===== PORTADA ===== */
    #portada {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: opacity 0.8s ease, transform 0.8s ease;
      overflow-y: auto;
      padding: 0;
    }

    .background-elements {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      z-index: 1;
      pointer-events: none;
    }

    .dna-strand {
      position: absolute;
      width: 2px;
      height: 150%;
      background: rgba(212, 175, 55, 0.2);
      transform: rotate(25deg);
      top: -25%;
    }

    .dna-strand:nth-child(1) { left: 15%; }
    .dna-strand:nth-child(2) { left: 30%; }
    .dna-strand:nth-child(3) { left: 50%; }
    .dna-strand:nth-child(4) { left: 70%; }
    .dna-strand:nth-child(5) { left: 85%; }

    .fossil-icon {
      position: absolute;
      font-size: 2rem;
      color: rgba(212, 175, 55, 0.3);
    }
    .fossil-icon:nth-child(6) { top: 20%; left: 10%; }
    .fossil-icon:nth-child(7) { top: 40%; left: 25%; }
    .fossil-icon:nth-child(8) { top: 60%; left: 80%; }
    .fossil-icon:nth-child(9) { top: 75%; left: 15%; }
    .fossil-icon:nth-child(10) { top: 30%; left: 90%; }

    .cover-container {
      position: relative;
      z-index: 10;
      max-width: 1200px;
      width: 90%;
      background: rgba(18, 30, 23, 0.97); /* Más opaco para mejor contraste */
      color: #fff;
      border-radius: 20px;
      padding: 32px 10px 24px 10px;
      box-shadow: 0 15px 50px rgba(0, 0, 0, 0.7);
      text-align: center;
      margin: 32px auto;
    }

    .university-header {
      margin-bottom: 30px;
      border-bottom: 2px solid #d4af37;
      padding-bottom: 20px;
    }

    .university-name {
      font-size: 2.8rem;
      font-weight: 700;
      color: #d4af37;
      letter-spacing: 1px;
      margin-bottom: 10px;
      text-transform: uppercase;
    }

    .faculty-info {
      font-size: 1.4rem;
      opacity: 0.9;
    }

    .main-title {
      font-size: 2.5rem;
      font-weight: 900;
      margin: 24px 0 12px 0;
      text-transform: uppercase;
      letter-spacing: 2px;
      text-shadow: 0 2px 8px #000, 0 4px 24px #d4af37;
      color: #fff;
    }

    .main-title::after {
      content: '';
      position: absolute;
      bottom: -15px;
      left: 50%;
      transform: translateX(-50%);
      width: 150px;
      height: 4px;
      background: linear-gradient(to right, #1a472a, #d4af37, #1a472a);
      border-radius: 2px;
    }

    .subtitle {
      font-size: 1.1rem;
      font-weight: 400;
      max-width: 800px;
      margin: 0 auto 24px;
      line-height: 1.6;
      color: #e6e6e6;
      background: rgba(18,30,23,0.7);
      border-radius: 12px;
      padding: 8px 10px;
      box-shadow: 0 2px 8px rgba(212,175,55,0.08);
    }

    .members-section {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 30px;
      margin: 40px 0;
    }

    .member-card {
      background: rgba(26, 71, 42, 0.15);
      border: 1px solid rgba(212, 175, 55, 0.15);
      color: #fff;
      border-radius: 15px;
      padding: 25px;
      width: 250px;
      transition: all 0.4s ease;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    }

    .member-card:hover {
      transform: translateY(-10px);
      background: rgba(26, 71, 42, 0.7);
      border-color: #d4af37;
      box-shadow: 0 10px 25px rgba(212, 175, 55, 0.2);
    }

    .member-icon {
      font-size: 3rem;
      color: #d4af37;
      margin-bottom: 20px;
    }

    .member-name {
      font-size: 1.4rem;
      font-weight: 600;
      margin-bottom: 10px;
    }

    .project-info {
      background: rgba(212, 175, 55, 0.1);
      border-radius: 15px;
      padding: 25px;
      max-width: 800px;
      margin: 40px auto 0 auto;
      border: 1px solid rgba(212, 175, 55, 0.2);
    }

    .info-item {
      margin: 15px 0;
      font-size: 1.2rem;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 15px;
    }

    .info-icon {
      color: #d4af37;
      font-size: 1.5rem;
    }

    .enter-button {
      font-size: 1.1rem;
      font-weight: 700;
      padding: 13px 28px;
      border-radius: 50px;
      margin-top: 18px;
      background: linear-gradient(135deg, #1a472a, #d4af37);
      color: #fff;
      box-shadow: 0 5px 20px rgba(26, 71, 42, 0.5);
      border: none;
      cursor: pointer;
      transition: background 0.3s, color 0.3s, transform 0.2s;
    }

    .enter-button:focus {
      outline: 2px solid #d4af37;
      outline-offset: 2px;
    }

    .enter-button:hover {
      background: linear-gradient(135deg, #d4af37, #1a472a);
      color: #fff;
      transform: translateY(-3px) scale(1.04);
    }

    .date-section {
      margin-top: 40px;
      font-size: 1.3rem;
      color: #d4af37;
      font-weight: 500;
      letter-spacing: 1px;
    }

    .footer-logo {
      margin-top: 50px;
      font-size: 3rem;
      color: #d4af37;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); opacity: 1; }
      50% { transform: scale(1.1); opacity: 0.8; }
    }

    /* ===== CONTENIDO PRINCIPAL ===== */
    #contenido-web {
      display: none;
      background-color: #f9f6ee;
      color: var(--color-text);
      background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 100 100"><rect width="100" height="100" fill="%23f9f6ee"/><path d="M0,0 L100,100 M100,0 L0,100" stroke="%23e8e1d1" stroke-width="0.5"/></svg>');
    }

    header {
      background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
      color: white;
      padding: 100px 20px 60px;
      text-align: center;
      position: relative;
      overflow: hidden;
      clip-path: polygon(0 0, 100% 0, 100% 90%, 0 100%);
    }

    .header-content {
      max-width: 1000px;
      margin: 0 auto;
      position: relative;
      z-index: 2;
    }

    h1 {
      font-size: 3.5rem;
      font-weight: 700;
      margin-bottom: 20px;
      letter-spacing: 1px;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
    }

    .subtitle {
      font-size: 1.5rem;
      font-weight: 300;
      max-width: 700px;
      margin: 0 auto;
      opacity: 0.9;
    }

    .header-decoration {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><path d="M20,20 Q40,5 60,20 T100,20" stroke="%23d4af37" stroke-width="1" fill="none" opacity="0.1"/></svg>');
      background-size: 200px;
      opacity: 0.2;
      z-index: 1;
    }

    nav {
      background-color: white;
      box-shadow: var(--shadow);
      position: sticky;
      top: 0;
      z-index: 1000;
    }

    .nav-container {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      padding: 15px 20px;
    }

    .nav-item {
      margin: 5px 15px;
      position: relative;
    }

    .nav-item a {
      color: var(--color-primary);
      text-decoration: none;
      font-weight: 600;
      font-size: 1.1rem;
      padding: 8px 5px;
      transition: var(--transition);
      display: block;
    }

    .nav-item a:hover {
      color: var(--color-accent);
    }

    .nav-item a::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 0;
      height: 3px;
      background-color: var(--color-accent);
      transition: var(--transition);
    }

    .nav-item a:hover::after {
      width: 100%;
    }

    .container {
      max-width: 1000px;
      margin: 50px auto;
      padding: 0 20px;
    }

    .section {
      background-color: white;
      border-radius: var(--radius);
      padding: 40px;
      margin-bottom: 50px;
      box-shadow: var(--shadow);
      position: relative;
      overflow: hidden;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    .section:hover {
      transform: translateY(-5px);
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
    }

    .section::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 5px;
      height: 100%;
      background: linear-gradient(to bottom, var(--color-primary), var(--color-accent));
    }

    .section-title {
      color: var(--color-primary);
      font-size: 2.2rem;
      margin-bottom: 25px;
      padding-bottom: 15px;
      border-bottom: 2px solid var(--color-accent);
      position: relative;
    }

    .section-title::after {
      content: '';
      position: absolute;
      bottom: -2px;
      left: 0;
      width: 80px;
      height: 2px;
      background-color: var(--color-accent);
    }

    .content-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 30px;
      margin: 30px 0;
    }

    @media (max-width: 768px) {
      .content-grid {
        grid-template-columns: 1fr;
      }
    }

    .text-content {
      font-size: 1.1rem;
    }

    .text-content p {
      margin-bottom: 20px;
    }

    .text-content ul {
      margin: 20px 0;
      padding-left: 25px;
    }

    .text-content li {
      margin-bottom: 10px;
      position: relative;
    }

    .text-content li::before {
      content: '•';
      color: var(--color-accent);
      font-weight: bold;
      position: absolute;
      left: -20px;
    }

    /* Imágenes mejoradas */
    .image-container {
      border-radius: var(--radius);
      overflow: hidden;
      box-shadow: var(--shadow);
      position: relative;
      height: 100%;
      min-height: 300px;
      display: flex;
      align-items: center;
      justify-content: center;
      background-color: #f5f2e9;
      transition: all 0.3s ease;
      background-size: cover;
      background-position: center;
    }

    .image-container:hover {
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
    }

    .image-container img {
      width: 100%;
      height: auto;
      display: block;
      transition: transform 0.5s ease;
      object-fit: cover;
      min-height: 300px;
    }

    .image-container:hover img {
      transform: scale(1.03);
    }

    .image-overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 60%, rgba(0, 0, 0, 0.7) 100%);
      padding: 20px;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      z-index: 2;
    }

    .image-title {
      color: white;
      font-size: 1.8rem;
      font-weight: bold;
      margin-bottom: 10px;
      text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
    }

    .image-description {
      color: white;
      font-size: 1.1rem;
      text-shadow: 0 1px 3px rgba(0, 0, 0, 0.5);
      max-width: 90%;
    }

    .image-annotation {
      position: absolute;
      background: rgba(212, 175, 55, 0.9);
      color: var(--color-primary);
      padding: 8px 15px;
      border-radius: 30px;
      font-weight: bold;
      font-size: 0.9rem;
      z-index: 10;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
    }

    .timeline {
      display: flex;
      flex-direction: column;
      margin: 40px 0;
      position: relative;
    }

    .timeline::before {
      content: '';
      position: absolute;
      top: 0;
      bottom: 0;
      left: 50%;
      width: 4px;
      background: linear-gradient(to bottom, var(--color-primary), var(--color-accent));
      transform: translateX(-50%);
    }

    .timeline-item {
      display: flex;
      margin-bottom: 40px;
      position: relative;
      width: 100%;
    }

    .timeline-item:nth-child(odd) {
      justify-content: flex-start;
    }

    .timeline-item:nth-child(even) {
      justify-content: flex-end;
    }

    .timeline-content {
      width: calc(50% - 40px);
      padding: 25px;
      background: white;
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      position: relative;
      border-left: 3px solid var(--color-accent);
      transition: transform 0.3s ease;
    }

    .timeline-content:hover {
      transform: scale(1.02);
    }

    .timeline-item:nth-child(even) .timeline-content {
      border-left: none;
      border-right: 3px solid var(--color-accent);
    }

    .timeline-year {
      font-weight: bold;
      color: var(--color-primary);
      font-size: 1.3rem;
      margin-bottom: 10px;
      display: flex;
      align-items: center;
    }

    .timeline-year i {
      margin-right: 10px;
      color: var(--color-accent);
    }

    .timeline-desc {
      font-size: 1rem;
      color: var(--color-text-light);
    }

    .chart-container {
      margin: 40px 0;
      background: white;
      padding: 25px;
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      transition: transform 0.3s ease;
    }

    .chart-container:hover {
      transform: translateY(-5px);
    }

    .chart-title {
      text-align: center;
      margin-bottom: 20px;
      color: var(--color-primary);
      font-size: 1.4rem;
    }

    .chart-wrapper {
      position: relative;
      height: 400px;
    }

    /* Sección especial para la encuesta */
    .survey-section {
      background: linear-gradient(135deg, rgba(26, 71, 42, 0.1), rgba(212, 175, 55, 0.1));
      border: 2px dashed var(--color-accent);
      border-radius: var(--radius);
      padding: 30px;
      margin: 40px 0;
      text-align: center;
      position: relative;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0% {
        box-shadow: 0 0 0 0 rgba(212, 175, 55, 0.4);
      }

      70% {
        box-shadow: 0 0 0 15px rgba(212, 175, 55, 0);
      }

      100% {
        box-shadow: 0 0 0 0 rgba(212, 175, 55, 0);
      }
    }

    .survey-title {
      color: var(--color-primary);
      font-size: 1.8rem;
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 15px;
    }

    .survey-description {
      font-size: 1.1rem;
      margin-bottom: 25px;
      color: var(--color-text-light);
      max-width: 800px;
      margin-left: auto;
      margin-right: auto;
    }

    .survey-link {
      display: inline-block;
      background: var(--color-accent);
      color: var(--color-primary);
      text-decoration: none;
      font-weight: bold;
      font-size: 1.2rem;
      padding: 15px 40px;
      border-radius: 50px;
      margin: 20px 0;
      transition: all 0.3s ease;
      box-shadow: 0 4px 15px rgba(212, 175, 55, 0.3);
      position: relative;
      overflow: hidden;
    }

    .survey-link::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
      transition: 0.5s;
    }

    .survey-link:hover::before {
      left: 100%;
    }

    .survey-link:hover {
      background: var(--color-primary);
      color: white;
      transform: translateY(-3px);
      box-shadow: 0 6px 20px rgba(26, 71, 42, 0.4);
    }

    .survey-icon {
      position: absolute;
      top: -20px;
      right: 20px;
      background: var(--color-accent);
      color: var(--color-primary);
      width: 60px;
      height: 60px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.8rem;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      animation: bounce 2s infinite;
    }

    @keyframes bounce {
      0%,
      20%,
      50%,
      80%,
      100% {
        transform: translateY(0);
      }

      40% {
        transform: translateY(-20px);
      }

      60% {
        transform: translateY(-10px);
      }
    }

    .bibliography {
      margin-top: 30px;
      padding-top: 20px;
      border-top: 1px solid #eee;
    }

    .biblio-item {
      margin-bottom: 15px;
      padding-left: 25px;
      position: relative;
    }

    .biblio-item::before {
      content: '📚';
      position: absolute;
      left: 0;
    }

    .biblio-item a {
      color: var(--color-primary);
      text-decoration: none;
      transition: var(--transition);
      font-weight: 500;
    }

    .biblio-item a:hover {
      color: var(--color-accent);
      text-decoration: underline;
    }

    .back-to-top {
      position: fixed;
      bottom: 30px;
      right: 30px;
      width: 50px;
      height: 50px;
      background: var(--color-primary);
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      cursor: pointer;
      box-shadow: var(--shadow);
      transition: var(--transition);
      z-index: 999;
      opacity: 0;
      transform: translateY(20px);
    }

    .back-to-top.visible {
      opacity: 1;
      transform: translateY(0);
    }

    .back-to-top:hover {
      background: var(--color-accent);
      transform: translateY(-5px);
    }

    footer {
      background: var(--color-dark);
      color: white;
      padding: 40px 20px;
      text-align: center;
      clip-path: polygon(0 20%, 100% 0, 100% 100%, 0 100%);
    }

    .footer-content {
      max-width: 1000px;
      margin: 0 auto;
      padding-top: 30px;
    }

    .footer-title {
      font-size: 1.8rem;
      margin-bottom: 20px;
      color: var(--color-accent);
    }

    .social-icons {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin: 25px 0;
    }

    .social-icons a {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 50px;
      height: 50px;
      background: rgba(255, 255, 255, 0.1);
      color: white;
      border-radius: 50%;
      font-size: 1.5rem;
      transition: all 0.3s ease;
    }

    .social-icons a:hover {
      background: var(--color-accent);
      color: var(--color-primary);
      transform: translateY(-5px);
    }

    .copyright {
      margin-top: 30px;
      padding-top: 20px;
      border-top: 1px solid rgba(255, 255, 255, 0.1);
      opacity: 0.7;
    }

    .quote-section {
      background: rgba(26, 71, 42, 0.05);
      border-left: 5px solid var(--color-accent);
      padding: 30px;
      margin: 40px 0;
      border-radius: var(--radius);
    }

    .quote-text {
      font-style: italic;
      font-size: 1.3rem;
      color: var(--color-primary);
      margin-bottom: 15px;
      text-align: center;
    }

    .quote-author {
      text-align: right;
      font-weight: bold;
      color: var(--color-secondary);
    }

    .evolution-stages {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 20px;
      margin: 40px 0;
    }

    .stage-card {
      background: white;
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 20px;
      text-align: center;
      transition: all 0.3s ease;
    }

    .stage-card:hover {
      transform: translateY(-10px);
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
    }

    .stage-icon {
      font-size: 2.5rem;
      color: var(--color-accent);
      margin-bottom: 15px;
    }

    .stage-name {
      font-weight: bold;
      color: var(--color-primary);
      margin-bottom: 5px;
    }

    .stage-period {
      font-size: 0.9rem;
      color: var(--color-text-light);
    }

    .contact-card {
      background: white;
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 30px;
      text-align: center;
      max-width: 600px;
      margin: 0 auto;
    }

    .contact-title {
      color: var(--color-primary);
      font-size: 1.8rem;
      margin-bottom: 25px;
    }

    .contact-info {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
      margin: 30px 0;
    }

    .contact-item {
      flex: 1;
      min-width: 200px;
      padding: 20px;
      background: rgba(26, 71, 42, 0.05);
      border-radius: var(--radius);
      transition: all 0.3s ease;
    }

    .contact-item:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
      background: rgba(26, 71, 42, 0.1);
    }

    .contact-icon {
      font-size: 2.5rem;
      color: var(--color-accent);
      margin-bottom: 15px;
    }

    .contact-label {
      font-weight: bold;
      color: var(--color-primary);
      margin-bottom: 10px;
    }

    .contact-link {
      color: var(--color-secondary);
      text-decoration: none;
      transition: all 0.3s ease;
    }

    .contact-link:hover {
      color: var(--color-accent);
      text-decoration: underline;
    }

    .metodo-btn {
      background: rgba(212, 175, 55, 0.95);
      color: #1a472a;
      font-weight: bold;
      font-size: 1.2rem;
      border-radius: 30px;
      padding: 15px 35px;
      box-shadow: 0 4px 16px rgba(0, 0, 0, 0.10);
      margin: 10px 0;
      text-align: center;
      transition: background 0.3s;
      border: none;
      cursor: pointer;
    }

    .metodo-btn:hover {
      background: #1a472a;
      color: #fff;
    }

    .explicacion-metodo {
      margin-top: 25px;
      background: #f5f5dc;
      border-radius: 10px;
      padding: 20px;
      min-height: 60px;
      color: #1a472a;
      font-size: 1.1rem;
      box-shadow: 0 2px 10px rgba(0,0,0,0.07);
      opacity: 1;
      transition: opacity 0.5s;
    }

    .explicacion-metodo.fade {
      opacity: 0;
    }

    .info-especie {
      margin-top: 25px;
      background: #f5f5dc;
      border-radius: 10px;
      padding: 20px;
      min-height: 60px;
      color: #1a472a;
      font-size: 1.1rem;
      box-shadow: 0 2px 10px rgba(0,0,0,0.07);
      opacity: 1;
      transition: opacity 0.5s;
    }

    .info-especie.fade {
      opacity: 0;
    }

    .comparacion-bg {
      position: relative;
      min-height: 350px;
      border-radius: 16px;
      overflow: hidden;
      background: #fff;
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.12);
      margin-bottom: 20px;
      padding: 40px 20px 30px 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .comparacion-titulo {
      width: 100%;
      text-align: center;
      color: #1a472a;
      font-size: 2rem;
      font-weight: 700;
      margin-top: 40px;
      margin-bottom: 8px;
      text-shadow: 0 2px 8px #fff;
    }

    .comparacion-desc {
      width: 100%;
      text-align: center;
      color: #333;
      font-size: 1.1rem;
      font-weight: 400;
      margin-bottom: 0;
      text-shadow: 0 2px 8px #fff;
    }

    .caract-btn {
      background: #d4af37;
      color: #1a472a;
      font-weight: bold;
      font-size: 1.1rem;
      border-radius: 30px;
      padding: 12px 28px;
      box-shadow: 0 4px 16px rgba(0,0,0,0.10);
      border: none;
      cursor: pointer;
      transition: background 0.3s, color 0.3s;
      margin-bottom: 10px;
    }

    .caract-btn:hover {
      background: #1a472a;
      color: #fff;
    }

    .info-caracteristica {
      margin-top: 25px;
      background: #f5f5dc;
      border-radius: 10px;
      padding: 20px;
      min-height: 60px;
      color: #1a472a;
      font-size: 1.1rem;
      box-shadow: 0 2px 10px rgba(0,0,0,0.07);
      opacity: 1;
      transition: opacity 0.5s;
    }

    .info-caracteristica.fade {
      opacity: 0;
    }

    /* ===== RESPONSIVE ===== */
    @media (max-width: 992px) {
      .cover-container { padding: 30px; }
      .main-title { font-size: 3.5rem; }
      .subtitle { font-size: 1.5rem; }
      .university-name { font-size: 2.2rem; }
      .faculty-info { font-size: 1.2rem; }
      h1 { font-size: 2.5rem; }
      .section-title { font-size: 1.8rem; }
      .survey-title { font-size: 1.5rem; }
      .survey-link { padding: 12px 30px; font-size: 1.1rem; }
    }

    @media (max-width: 768px) {
      .main-title { font-size: 2.8rem; }
      .subtitle { font-size: 1.3rem; }
      .member-card { width: 100%; max-width: 300px; }
      .project-info { padding: 20px; }
      .info-item { font-size: 1.1rem; }
      .section { padding: 30px 20px; }
      .timeline::before { left: 20px; }
      .timeline-content {
        width: calc(100% - 60px);
        margin-left: 40px;
        border-left: 3px solid var(--color-accent);
        border-right: none;
      }
      .timeline-item:nth-child(even) .timeline-content {
        border-left: 3px solid var(--color-accent);
        border-right: none;
      }
    }

    @media (max-width: 480px) {
      .cover-container { padding: 20px; }
      .main-title { font-size: 2.2rem; }
      .subtitle { font-size: 1.1rem; }
      .university-name { font-size: 1.8rem; }
      .enter-button { padding: 15px 30px; font-size: 1.1rem; }
      .section-title { font-size: 1.6rem; }
    }
  </style>
</head>

<body>
  <!-- PORTADA -->
  <div id="portada">
    <div class="background-elements">
      <div class="dna-strand"></div>
      <div class="dna-strand"></div>
      <div class="dna-strand"></div>
      <div class="dna-strand"></div>
      <div class="dna-strand"></div>
      <i class="fas fa-bone fossil-icon"></i>
      <i class="fas fa-skull fossil-icon"></i>
      <i class="fas fa-footprints fossil-icon"></i>
      <i class="fas fa-history fossil-icon"></i>
      <i class="fas fa-seedling fossil-icon"></i>
    </div>

    <div class="cover-container">
      <div class="university-header">
        <h1 class="university-name">Universidad Martin Lutero</h1>
        <p class="faculty-info">Facultad de Ingeniería - Carrera: Ingeniería en Sistemas</p>
      </div>

      <h1 class="main-title">Evolución Humana</h1>
      <p class="subtitle">Estudio científico de la metamorfosis biológica y el desarrollo cultural de nuestra especie</p>

      <div class="members-section">
        <div class="member-card">
          <div class="member-icon">
            <i class="fas fa-user-graduate"></i>
          </div>
          <h3 class="member-name">Ileana Alfaro</h3>
          <p>Ingeniería en Sistemas</p>
        </div>
        <div class="member-card">
          <div class="member-icon">
            <i class="fas fa-user-graduate"></i>
          </div>
          <h3 class="member-name">Esleydi Herrera</h3>
          <p>Ingeniería en Sistemas</p>
        </div>
        <div class="member-card">
          <div class="member-icon">
            <i class="fas fa-user-graduate"></i>
          </div>
          <h3 class="member-name">Ester Carrasco</h3>
          <p>Ingeniería en Sistemas</p>
        </div>
        <div class="member-card">
          <div class="member-icon">
            <i class="fas fa-user-graduate"></i>
          </div>
          <h3 class="member-name">Cristopher Valladares</h3>
          <p>Ingeniería en Sistemas</p>
        </div>
      </div>

      <div class="project-info">
        <div class="info-item">
          <i class="fas fa-graduation-cap info-icon"></i>
          <span>Segundo Año - Ingeniería en Sistemas</span>
        </div>
        <div class="info-item">
          <i class="fas fa-calendar-alt info-icon"></i>
          <span>Fecha: 21 de junio del 2025</span>
        </div>
        <div class="info-item">
          <i class="fas fa-book info-icon"></i>
          <span>Proyecto de Investigación Científica</span>
        </div>
      </div>

      <button class="enter-button" type="button" id="comenzarBtn">
        Acceder al Estudio Completo
        <i class="fas fa-arrow-right"></i>
      </button>

      <div class="date-section">
        <i class="fas fa-clock"></i> Presentación: Junio 2025
      </div>

      <div class="footer-logo">
        <i class="fas fa-brain"></i>
      </div>
    </div>
  </div>

  <!-- CONTENIDO PRINCIPAL -->
  <div id="contenido-web">
    <header>
      <div class="header-decoration"></div>
      <div class="header-content">
        <h1>Evolución Humana</h1>
        <p class="subtitle">Metamorfosis Biológica y Desarrollo Cultural</p>
      </div>
    </header>
    
    <nav>
      <div class="nav-container">
        <div class="nav-item"><a href="#origen"><i class="fas fa-seedling"></i> Origen</a></div>
        <div class="nav-item"><a href="#metodo"><i class="fas fa-flask"></i> Método</a></div>
        <div class="nav-item"><a href="#teorias"><i class="fas fa-brain"></i> Teorías</a></div>
        <div class="nav-item"><a href="#linea-tiempo"><i class="fas fa-hourglass-half"></i> Línea de Tiempo</a></div>
        <div class="nav-item"><a href="#graficos"><i class="fas fa-chart-bar"></i> Gráficos</a></div>
        <div class="nav-item"><a href="#encuesta"><i class="fas fa-poll"></i> Encuesta</a></div>
        <div class="nav-item"><a href="#citas"><i class="fas fa-quote-right"></i> Citas</a></div>
        <div class="nav-item"><a href="#bibliografia"><i class="fas fa-book"></i> Bibliografía</a></div>
        <!-- <div class="nav-item"><a href="#contacto"><i class="fas fa-envelope"></i> Contacto</a></div> -->
      </div>
    </nav>
    
    <div class="container">
      <section id="origen" class="section">
        <h2 class="section-title">Origen y Evolución Humana</h2>
        
        <div class="content-grid">
          <div class="text-content">
            <p>La evolución del hombre, conocida como hominización, describe las transformaciones biológicas, anatómicas y culturales que dieron origen al Homo sapiens. Inició hace unos 6 millones de años en África, donde nuestros antecesores primates se dividieron en diferentes linajes.</p>
            
            <p>Uno de estos linajes desarrolló características fundamentales:</p>
            <ul>
              <li><strong>Bipedismo:</strong> Capacidad para caminar sobre dos piernas, liberando las manos para manipular objetos</li>
              <li><strong>Uso de herramientas:</strong> Fabricación y utilización de instrumentos para cazar y procesar alimentos</li>
              <li><strong>Cerebro complejo:</strong> Desarrollo gradual de capacidades cognitivas superiores como pensamiento abstracto</li>
              <li><strong>Comunicación avanzada:</strong> Evolución del lenguaje articulado y sistemas simbólicos complejos</li>
            </ul>
          </div>
          
          <div class="image-container">
            <img src="https://images.unsplash.com/photo-1590698933947-a202b069a861?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80" alt="Árbol Filogenético Humano" loading="lazy">
            <div class="image-overlay">
              <div class="image-title">Árbol Filogenético Humano</div>
              <div class="image-description">Relación evolutiva entre diferentes especies de homínidos desde los primates hasta el Homo sapiens</div>
            </div>
            <div class="image-annotation" style="top: 30px; left: 30px;">Primates</div>
            <div class="image-annotation" style="top: 100px; left: 80px;">Australopithecus</div>
            <div class="image-annotation" style="top: 180px; left: 130px;">Homo habilis</div>
            <div class="image-annotation" style="top: 260px; left: 180px;">Homo sapiens</div>
          </div>
        </div>
      </section>

      <section id="metodo" class="section">
        <h2 class="section-title">El Método Científico y la Evolución</h2>
        <div style="position: relative; min-height: 350px; border-radius: 16px; overflow: hidden; background: url('https://images.unsplash.com/photo-1581092335397-9fa06a5a1b2e?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80') center/cover no-repeat; box-shadow: 0 8px 32px rgba(0,0,0,0.12); margin-bottom: 20px;">
          <div style="position: absolute; top: 30px; left: 40px;">
            <button class="metodo-btn" onclick="mostrarPaso('observacion')">Observación</button>
          </div>
          <div style="position: absolute; top: 30px; right: 40px;">
            <button class="metodo-btn" onclick="mostrarPaso('hipotesis')">Hipótesis</button>
          </div>
          <div style="position: absolute; bottom: 80px; left: 40px;">
            <button class="metodo-btn" onclick="mostrarPaso('experimentacion')">Experimentación</button>
          </div>
          <div style="position: absolute; bottom: 80px; right: 40px;">
            <button class="metodo-btn" onclick="mostrarPaso('conclusion')">Conclusión</button>
          </div>
          <div style="position: absolute; bottom: 20px; left: 0; width: 100%; text-align: center; color: #fff; text-shadow: 0 2px 8px #000; font-size: 1.2rem; font-weight: 500; background: linear-gradient(transparent 60%, rgba(0,0,0,0.5) 100%); padding: 20px 0 0 0;">
            Metodología científica aplicada al estudio de la evolución humana
          </div>
        </div>
        <div id="explicacion-metodo" class="explicacion-metodo">
          Haz clic en cada etapa para ver su explicación.
        </div>

        <div style="margin-top: 25px;">
          <ul style="list-style: disc; padding-left: 25px; color: #1a472a; font-size: 1.08rem;">
            <li><b>Observación:</b> Se recopilan datos y se identifican fenómenos o patrones relacionados con la evolución humana, como fósiles, herramientas y restos genéticos.</li>
            <li><b>Hipótesis:</b> Se plantea una posible explicación sobre el origen o desarrollo de los homínidos, por ejemplo, cómo el bipedismo favoreció la supervivencia.</li>
            <li><b>Experimentación:</b> Se diseñan investigaciones, análisis de fósiles, ADN y simulaciones para poner a prueba las hipótesis propuestas.</li>
            <li><b>Conclusión:</b> Se analizan los resultados obtenidos y se determina si la hipótesis es válida, ajustando el conocimiento científico sobre la evolución humana.</li>
          </ul>
        </div>
      </section>

      <section id="teorias" class="section">
        <h2 class="section-title">Teorías Evolutivas y Descubrimientos</h2>
        
        <div class="content-grid">
          <div class="text-content">
            <p>Charles Darwin sentó las bases de la teoría evolutiva moderna al proponer que los humanos descienden de un ancestro común con los simios. Sus observaciones revolucionaron nuestra comprensión del origen humano.</p>
            
            <p>Las teorías modernas incluyen:</p>
            <ul>
              <li><strong>Genética de poblaciones:</strong> Estudio de variaciones genéticas en grupos humanos actuales y ancestrales</li>
              <li><strong>Selección natural:</strong> Mecanismos adaptativos que favorecieron ciertos rasgos en ambientes específicos</li>
              <li><strong>Evolución cultural:</strong> Transmisión no genética de conocimientos y comportamientos entre generaciones</li>
              <li><strong>Teoría del simio acuático:</strong> Propuesta controvertida sobre una fase acuática en la evolución humana</li>
            </ul>
            
            <p>Descubrimientos clave como los fósiles de Lucy (Australopithecus afarensis), Homo habilis y el Hombre de Neanderthal han ampliado nuestro conocimiento sobre el linaje humano.</p>
          </div>
          
          <div class="image-container">
            <img src="https://images.unsplash.com/photo-1620641788421-7a1c342ea42e?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80" alt="Comparación de especies homínidas" loading="lazy">
            <div class="image-overlay">
              <div class="image-title">Comparación de Especies</div>
              <div class="image-description">Diferencias anatómicas clave entre homínidos tempranos y modernos</div>
            </div>
            <div class="image-annotation" style="top: 50px; left: 50px;">Australopithecus</div>
            <div class="image-annotation" style="top: 50px; right: 50px;">Homo habilis</div>
            <div class="image-annotation" style="bottom: 80px; left: 50px;">Homo erectus</div>
            <div class="image-annotation" style="bottom: 80px; right: 50px;">Homo sapiens</div>
          </div>
        </div>
      </section>

      <section id="linea-tiempo" class="section">
        <h2 class="section-title">Hitos Evolutivos Relevantes</h2>
        <div class="timeline">
          <div class="timeline-item">
            <div class="timeline-content">
              <div class="timeline-year"><i class="fas fa-dna"></i> 7M años</div>
              <div class="timeline-desc">Primeros homínidos aparecen en África.</div>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-content">
              <div class="timeline-year"><i class="fas fa-paw"></i> 4.4M años</div>
              <div class="timeline-desc">Ardipithecus ramidus: uno de los primeros bípedos conocidos.</div>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-content">
              <div class="timeline-year"><i class="fas fa-user"></i> 3.2M años</div>
              <div class="timeline-desc">Australopithecus afarensis (“Lucy”): bipedismo consolidado.</div>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-content">
              <div class="timeline-year"><i class="fas fa-tools"></i> 2.8M años</div>
              <div class="timeline-desc">Homo habilis: uso de herramientas de piedra.</div>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-content">
              <div class="timeline-year"><i class="fas fa-fire"></i> 1.8M años</div>
              <div class="timeline-desc">Homo erectus: control del fuego y migración fuera de África.</div>
            </div>
          </div>
          <div class="timeline-item">
            <div class="timeline-content">
              <div class="timeline-year"><i class="fas fa-brain"></i> 300K años</div>
              <div class="timeline-desc">Aparición de Homo sapiens: pensamiento simbólico y arte rupestre.</div>
            </div>
          </div>
        </div>
      </section>

      <section id="graficos" class="section">
        <h2 class="section-title">Análisis Gráfico de la Evolución</h2>
        
        <div class="chart-container">
          <div class="chart-title">Capacidad Craneal en la Evolución Humana</div>
          <div class="chart-wrapper">
            <canvas id="cranialChart"></canvas>
          </div>
        </div>
        
        <div class="chart-container">
          <div class="chart-title">Distribución de Hitos Evolutivos</div>
          <div class="chart-wrapper">
            <canvas id="milestonesChart"></canvas>
          </div>
        </div>
        
        <div class="chart-container">
          <div class="chart-title">Comparación de Especies Humanas</div>
          <div class="chart-wrapper">
            <canvas id="speciesChart"></canvas>
          </div>
        </div>
      </section>

      <section id="encuesta" class="section">
        <h2 class="section-title">Participa en Nuestra Encuesta</h2>
        
        <div class="survey-section">
          <div class="survey-icon">
            <i class="fas fa-poll"></i>
          </div>
          
          <h3 class="survey-title">
            <i class="fas fa-clipboard-list"></i>
            Encuesta sobre la Teoría de la Evolución Humana
          </h3>
          
          <p class="survey-description">
            Tu opinión es importante para nuestra investigación. Participa en nuestra encuesta sobre las teorías de la evolución humana y ayúdanos a comprender mejor la percepción pública sobre este fascinante tema científico.
          </p>
          
          <p class="survey-description">
            La encuesta incluye preguntas sobre:
          </p>
          
          <ul style="text-align: left; max-width: 600px; margin: 20px auto;">
            <li>Conocimiento sobre teorías evolutivas</li>
            <li>Percepción de la evidencia científica</li>
            <li>Impacto de la evolución humana en la sociedad moderna</li>
            <li>Perspectivas sobre descubrimientos recientes</li>
          </ul>
          
          <a href="https://qt18r7ih.forms.app/encuesta-sobre-la-teoria-de-la-evolucion-humana/report" class="survey-link" target="_blank" rel="noopener noreferrer">
            <i class="fas fa-external-link-alt"></i> Ver Resultados de la Encuesta
          </a>
          
          <p style="margin-top: 20px; font-style: italic;">
            ¡Tus respuestas son anónimas y contribuirán a nuestra investigación académica!
          </p>
        </div>
      </section>

      <section id="citas" class="section">
        <h2 class="section-title">Citas Inspiradoras</h2>
        <div class="image-container">
          <img src="https://images.unsplash.com/photo-1506784983877-45594efa4cbe?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80" alt="Citas sobre evolución" loading="lazy">
          <div class="image-overlay" style="background: rgba(0,0,0,0.7); justify-content: center;">
            <div class="quote-section" style="background: rgba(255,255,255,0.92); color: #1a472a; margin: 10px auto; max-width: 600px;">
              <div class="quote-text">"Nada tiene sentido en biología si no es a la luz de la evolución."</div>
              <div class="quote-author">— Theodosius Dobzhansky</div>
            </div>
            <div class="quote-section" style="background: rgba(255,255,255,0.92); color: #1a472a; margin: 10px auto; max-width: 600px;">
              <div class="quote-text">"No es la especie más fuerte la que sobrevive, ni la más inteligente, sino la que mejor responde al cambio."</div>
              <div class="quote-author">— Charles Darwin</div>
            </div>
            <div class="quote-section" style="background: rgba(255,255,255,0.92); color: #1a472a; margin: 10px auto; max-width: 600px;">
              <div class="quote-text">"La evolución no es una teoría, es un hecho."</div>
              <div class="quote-author">— Stephen Jay Gould</div>
            </div>
          </div>
        </div>
      </section>

      <section id="bibliografia" class="bibliography section">
        <h2 class="section-title">Bibliografía</h2>
        <ul>
          <li class="biblio-item">
            <a href="https://humanidades.com/evolucion-humana/" target="_blank" rel="noopener noreferrer">
              Evolución Humana - Origen y características. Enciclopedia Humanidades
            </a>
          </li>
          <li class="biblio-item">
            <a href="https://www.nationalgeographic.es/historia/origenes-humanidad-conceptos-basicos-evolucion" target="_blank" rel="noopener noreferrer">
              Orígenes de la humanidad: conceptos básicos sobre la evolución. National Geographic
            </a>
          </li>
          <li class="biblio-item">
            <a href="https://www.politicas.unam.mx/cea/wp-content/uploads/2023/08/2215_Evolucion_Humana_y_Diversidad_Cultural-1" target="_blank" rel="noopener noreferrer">
              Evolución Humana y Diversidad Cultural. UNAM
            </a>
          </li>
          <li class="biblio-item">
            <a href="https://academia-lab.com/enciclopedia/evolucion-humana/" target="_blank" rel="noopener noreferrer">
              Evolución Humana: qué es, características y etapas. Academia Lab
            </a>
          </li>
          <li class="biblio-item">
            <a href="https://www.diferenciador.com/evolucion-del-hombre/" target="_blank" rel="noopener noreferrer">
              Evolución del Hombre: Características y Etapas. Diferenciador
            </a>
          </li>
        </ul>
      </section>

      <div class="back-to-top" id="backToTop">
        <i class="fas fa-arrow-up"></i>
      </div>
      
      <footer>
        <div class="footer-content">
          <div class="footer-title">Evolución Humana</div>
          <p>Estudio científico de nuestro origen y desarrollo como especie</p>
          <div class="social-icons">
            <a href="mailto:vallecristopher102@gmail.com"><i class="fas fa-envelope"></i></a>
            <a href="https://github.com/cristopher281" target="_blank" rel="noopener noreferrer"><i class="fab fa-github"></i></a>
            <a href="https://www.youtube.com/@CristopherValle-nic" target="_blank" rel="noopener noreferrer"><i class="fab fa-youtube"></i></a>
          </div>
          <div class="copyright">
            © 2025 Proyecto de Cris y su equipo - Todos los derechos reservados
          </div>
        </div>
      </footer>
    </div>
    
    <script>
      // Registrar el plugin de etiquetas
      Chart.register(ChartDataLabels);

      // Gráfico de capacidad craneal
      const cranialCtx = document.getElementById('cranialChart').getContext('2d');
      new Chart(cranialCtx, {
        type: 'line',
        data: {
          labels: ['Australopithecus', 'H. habilis', 'H. erectus', 'H. neanderthal', 'H. sapiens'],
          datasets: [{
            label: 'Capacidad craneal (cm³)',
            data: [450, 610, 950, 1450, 1350],
            backgroundColor: 'rgba(42, 102, 64, 0.2)',
            borderColor: 'rgba(42, 102, 64, 1)',
            borderWidth: 3,
            pointBackgroundColor: 'rgba(212, 175, 55, 1)',
            pointBorderColor: '#fff',
            pointHoverRadius: 8,
            pointRadius: 6,
            tension: 0.2,
            fill: true
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          scales: {
            y: {
              beginAtZero: true,
              title: {
                display: true,
                text: 'Capacidad Craneal (cm³)',
                font: {
                  size: 14,
                  weight: 'bold'
                }
              },
              grid: {
                color: 'rgba(0, 0, 0, 0.05)'
              }
            },
            x: {
              grid: {
                display: false
              }
            }
          },
          plugins: {
            legend: {
              position: 'top',
              labels: {
                font: {
                  size: 14
                }
              }
            },
            title: {
              display: true,
              text: 'Evolución de la capacidad craneal en homínidos',
              font: {
                size: 18,
                weight: 'bold'
              },
              padding: 20
            },
            tooltip: {
              backgroundColor: 'rgba(26, 71, 42, 0.9)',
              titleFont: {
                size: 16
              },
              bodyFont: {
                size: 14
              }
            },
            datalabels: {
              anchor: 'end',
              align: 'top',
              formatter: (value) => value + ' cm³',
              font: {
                weight: 'bold',
                size: 12
              }
            }
          }
        },
        plugins: [ChartDataLabels]
      });

      // Gráfico de hitos evolutivos
      const milestonesCtx = document.getElementById('milestonesChart').getContext('2d');
      new Chart(milestonesCtx, {
        type: 'bar',
        data: {
          labels: ['Bipedismo', 'Herramientas', 'Fuego', 'Lenguaje', 'Arte', 'Agricultura'],
          datasets: [{
            label: 'Importancia evolutiva (%)',
            data: [25, 20, 15, 15, 10, 15],
            backgroundColor: [
              'rgba(42, 102, 64, 0.8)',
              'rgba(52, 132, 84, 0.8)',
              'rgba(72, 162, 104, 0.8)',
              'rgba(212, 175, 55, 0.8)',
              'rgba(180, 140, 35, 0.8)',
              'rgba(150, 110, 25, 0.8)'
            ],
            borderColor: [
              'rgba(42, 102, 64, 1)',
              'rgba(52, 132, 84, 1)',
              'rgba(72, 162, 104, 1)',
              'rgba(212, 175, 55, 1)',
              'rgba(180, 140, 35, 1)',
              'rgba(150, 110, 25, 1)'
            ],
            borderWidth: 1
          }]
        },
        options: {
          indexAxis: 'y',
          responsive: true,
          maintainAspectRatio: false,
          scales: {
            x: {
              beginAtZero: true,
              max: 30,
              title: {
                display: true,
                text: 'Importancia (%)',
                font: {
                  size: 14,
                  weight: 'bold'
                }
              },
              grid: {
                color: 'rgba(0, 0, 0, 0.05)'
              }
            },
            y: {
              grid: {
                display: false
              }
            }
          },
          plugins: {
            legend: {
              position: 'top',
              labels: {
                font: {
                  size: 14
                }
              }
            },
            title: {
              display: true,
              text: 'Importancia relativa de hitos evolutivos',
              font: {
                size: 18,
                weight: 'bold'
              },
              padding: 20
            },
            tooltip: {
              backgroundColor: 'rgba(26, 71, 42, 0.9)',
              titleFont: {
                size: 16
              },
              bodyFont: {
                size: 14
              }
            },
            datalabels: {
              anchor: 'end',
              align: 'end',
              formatter: (value) => value + '%',
              font: {
                weight: 'bold',
                size: 12
              }
            }
          }
        },
        plugins: [ChartDataLabels]
      });

      // Gráfico de comparación de especies
      const speciesCtx = document.getElementById('speciesChart').getContext('2d');
      new Chart(speciesCtx, {
        type: 'radar',
        data: {
          labels: ['Capacidad craneal', 'Altura', 'Herramientas', 'Distribución geográfica', 'Sofisticación cultural'],
          datasets: [
            {
              label: 'Homo habilis',
              data: [3, 2, 4, 3, 2],
              backgroundColor: 'rgba(42, 102, 64, 0.2)',
              borderColor: 'rgba(42, 102, 64, 1)',
              pointBackgroundColor: 'rgba(42, 102, 64, 1)',
              pointBorderColor: '#fff'
            },
            {
              label: 'Homo erectus',
              data: [5, 6, 7, 8, 4],
              backgroundColor: 'rgba(212, 175, 55, 0.2)',
              borderColor: 'rgba(212, 175, 55, 1)',
              pointBackgroundColor: 'rgba(212, 175, 55, 1)',
              pointBorderColor: '#fff'
            },
            {
              label: 'Homo sapiens',
              data: [9, 7, 9, 10, 10],
              backgroundColor: 'rgba(26, 71, 42, 0.2)',
              borderColor: 'rgba(26, 71, 42, 1)',
              pointBackgroundColor: 'rgba(26, 71, 42, 1)',
              pointBorderColor: '#fff'
            }
          ]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          scales: {
            r: {
              angleLines: {
                display: true
              },
              suggestedMin: 0,
              suggestedMax: 10,
              ticks: {
                stepSize: 2
              }
            }
          },
          plugins: {
            legend: {
              position: 'top',
              labels: {
                font: {
                  size: 14
                }
              }
            },
            title: {
              display: true,
              text: 'Comparación de características entre especies humanas',
              font: {
                size: 18,
                weight: 'bold'
              },
              padding: 20
            },
            tooltip: {
              backgroundColor: 'rgba(26, 71, 42, 0.9)',
              titleFont: {
                size: 16
              },
              bodyFont: {
                size: 14
              }
            }
          }
        }
      });

      // Botón para volver arriba
      const backToTopBtn = document.getElementById('backToTop');
      window.addEventListener('scroll', () => {
        if (window.pageYOffset > 300) {
          backToTopBtn.classList.add('visible');
        } else {
          backToTopBtn.classList.remove('visible');
        }
      });
      backToTopBtn.addEventListener('click', () => {
        window.scrollTo({ top: 0, behavior: 'smooth' });
      });

      // Efecto de aparición suave para las secciones
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.style.opacity = 1;
            entry.target.style.transform = 'translateY(0)';
          }
        });
      }, { threshold: 0.1 });
      document.querySelectorAll('.section').forEach(section => {
        section.style.opacity = 0;
        section.style.transform = 'translateY(20px)';
        section.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
        observer.observe(section);
      });

      // Funciones interactivas
      function mostrarPaso(paso) {
        const explicacion = {
          observacion: "Observación: Se recopilan datos y se identifican fenómenos o patrones relacionados con la evolución humana.",
          hipotesis: "Hipótesis: Se plantea una posible explicación o respuesta basada en la observación realizada.",
          experimentacion: "Experimentación: Se diseñan y realizan experimentos o investigaciones para poner a prueba la hipótesis.",
          conclusion: "Conclusión: Se analizan los resultados y se determina si la hipótesis es válida o debe modificarse."
        };
        const div = document.getElementById('explicacion-metodo');
        div.classList.add('fade');
        setTimeout(() => {
          div.textContent = explicacion[paso];
          div.classList.remove('fade');
        }, 400);
      }

      // Animación para los elementos de ADN en la portada (optimizada)
      const dnaStrands = document.querySelectorAll('.dna-strand');
      dnaStrands.forEach((strand) => {
        const fragment = document.createDocumentFragment();
        for (let i = 0; i < 15; i++) {
          const node = document.createElement('div');
          node.style.position = 'absolute';
          node.style.width = '12px';
          node.style.height = '12px';
          node.style.background = '#d4af37';
          node.style.borderRadius = '50%';
          node.style.top = (i * 60) + 'px';
          node.style.left = '-5px';
          node.style.opacity = '0.7';
          fragment.appendChild(node);
        }
        strand.appendChild(fragment);
      });

      // Función para cerrar la portada (solo con botón)
      let portadaCerrada = false;
      function cerrarPortada() {
        if (portadaCerrada) return;
        portadaCerrada = true;
        const portada = document.getElementById('portada');
        portada.style.opacity = '0';
        portada.style.transform = 'scale(1.1)';
        setTimeout(() => {
          portada.style.display = 'none';
          const contenido = document.getElementById('contenido-web');
          contenido.style.display = 'block';
          contenido.style.opacity = 0;
          setTimeout(() => {
            contenido.style.transition = 'opacity 1s';
            contenido.style.opacity = 1;
          }, 10);
          document.body.style.overflow = 'auto';
        }, 800);
      }

      // Evento para cerrar la portada SOLO con el botón
      document.getElementById('comenzarBtn').addEventListener('click', cerrarPortada);

      // Bloquea el scroll mientras la portada está activa
      document.body.style.overflow = 'hidden';

      // Accesibilidad: enfoca el botón al cargar
      window.addEventListener('DOMContentLoaded', () => {
        document.getElementById('comenzarBtn').focus();
      });
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Logísticas y Suministros Tangram S.A.S</title>
  <meta name="description" content="Logísticas y Suministros Tangram S.A.S - Mantenimiento de maquinaria amarilla. Sora y Tunja.">
  <style>
    :root{
      --bg:#050505;
      --neon:#fcd400;
      --muted:#9aa0a6;
      --panel: rgba(255,255,255,0.02);
      --radius:12px;
      --maxw:1100px;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, Arial;
      background:
        radial-gradient(900px 320px at 10% 10%, rgba(252,212,0,0.03), transparent 8%),
        linear-gradient(180deg,#030303,#050505);
      color:#eee;
      -webkit-font-smoothing:antialiased;
      line-height:1.45;
      overflow-x:hidden;
    }

    /* subtle animated background glow */
    .bg-anim{
      position:fixed;left:-20%;top:-40%;width:160%;height:160%;pointer-events:none;z-index:0;mix-blend-mode:screen;opacity:0.08;
      background:
        radial-gradient(300px 200px at 10% 20%, rgba(252,212,0,0.25), transparent 10%),
        radial-gradient(250px 150px at 80% 80%, rgba(200,200,200,0.12), transparent 10%),
        radial-gradient(220px 120px at 60% 30%, rgba(255,215,0,0.08), transparent 10%);
      animation: drift 18s linear infinite;
    }
    @keyframes drift{
      0%{transform:translateY(0) translateX(0) rotate(0deg)}
      50%{transform:translateY(10vh) translateX(-6vw) rotate(3deg)}
      100%{transform:translateY(0) translateX(0) rotate(0deg)}
    }

    /* NAV */
    .nav-wrap{
      position:fixed;top:0;left:0;right:0;z-index:220;
      backdrop-filter: blur(6px);
      background: linear-gradient(180deg, rgba(5,5,5,0.96), rgba(5,5,5,0.82));
      border-bottom: 1px solid rgba(252,212,0,0.05);
      box-shadow: 0 8px 40px rgba(0,0,0,0.6);
    }
    .nav{
      max-width:var(--maxw);margin:0 auto;display:flex;align-items:center;justify-content:space-between;padding:10px 14px;
      position:relative;z-index:230;
    }
    .brand{display:flex;align-items:center;gap:12px}
    .logo{
      width:56px;height:56px;border-radius:12px;background:linear-gradient(180deg,var(--neon), #ffd34d);
      color:#050505;font-weight:900;display:flex;align-items:center;justify-content:center;font-size:22px;
      box-shadow:0 8px 30px rgba(252,212,0,0.12), inset 0 -6px 14px rgba(0,0,0,0.18);
    }
    .brand .title{font-weight:800;font-size:0.98rem;color:#fff}
    .brand .sub{font-size:0.72rem;color:var(--muted);margin-top:2px}

    .menu{display:flex;gap:8px;align-items:center}
    .menu a{
      color:var(--neon);text-decoration:none;font-weight:700;padding:8px 12px;border-radius:10px;font-size:0.92rem;
      display:flex;gap:8px;align-items:center;transition:all .16s ease;text-shadow:0 0 8px rgba(252,212,0,0.06);
    }
    .menu a:hover{transform:translateY(-3px);box-shadow:0 12px 30px rgba(252,212,0,0.06)}
    .menu a.active{background:rgba(252,212,0,0.06);color:#fff}

    .hamburger{display:none;flex-direction:column;gap:5px;cursor:pointer;padding:6px}
    .hamburger span{width:28px;height:3px;background:var(--neon);border-radius:3px;display:block;box-shadow:0 1px 8px rgba(252,212,0,0.12)}

    /* Drawer (right) */
    .drawer {
      position:fixed;top:0;right:-100%;height:100vh;width:86%;max-width:380px;background:linear-gradient(180deg,#0a0a0a,#050505);
      box-shadow: -20px 40px 120px rgba(0,0,0,0.7);z-index:400;padding:18px;transition:right .32s cubic-bezier(.2,.9,.2,1);
      border-left:1px solid rgba(252,212,0,0.04);display:flex;flex-direction:column;gap:10px;
    }
    .drawer.open{right:0}
    .drawer .close{align-self:flex-end;font-size:22px;color:var(--neon);cursor:pointer}
    .drawer a{color:var(--neon);text-decoration:none;font-weight:800;padding:12px;border-radius:8px;display:flex;gap:8px;align-items:center}
    .drawer a:hover{background:rgba(252,212,0,0.03)}

    /* HERO */
    header.hero{
      padding:120px 18px 36px;
      text-align:center;
      color:#fff;
    }
    .big-name{
      font-size:1.6rem;font-weight:900;letter-spacing:0.6px;color:white;display:inline-block;padding:12px 18px;border-radius:14px;
      background: linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      box-shadow: 0 12px 50px rgba(252,212,0,0.06), 0 0 40px rgba(252,212,0,0.04) inset;
      text-shadow: 0 0 18px rgba(252,212,0,0.12);
      opacity:0; transform:translateY(8px);
      transition:all .9s cubic-bezier(.2,.9,.2,1);
    }
    .big-name.show{opacity:1;transform:none}
    .big-name .glow{color:var(--neon);text-shadow:0 0 18px rgba(252,212,0,0.6)}
    .hero p{margin:10px auto 0;color:var(--muted);max-width:760px}
    .hero .badge{display:inline-block;margin-top:14px;padding:8px 12px;border-radius:20px;background:linear-gradient(90deg, rgba(252,212,0,0.08), rgba(252,212,0,0.02));color:var(--neon);font-weight:800}

    main{max-width:var(--maxw);margin:18px auto;padding:0 14px 120px;position:relative;z-index:10}

    /* Sections */
    section.card{
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius:12px;padding:16px;margin-bottom:16px;border:1px solid rgba(255,255,255,0.03);
      box-shadow: 0 12px 40px rgba(0,0,0,0.5);overflow:hidden;
    }
    h2{color:var(--neon);margin:0 0 8px;font-size:1.05rem}
    p.lead{color:var(--muted);margin:0 0 10px}

    /* Services */
    .services{display:grid;gap:12px;grid-template-columns:repeat(auto-fit,minmax(220px,1fr))}
    .svc{padding:12px;border-radius:10px;background:var(--panel);border:1px solid rgba(255,255,255,0.03);transition:transform .18s ease}
    .svc:hover{transform:translateY(-8px);box-shadow:0 24px 60px rgba(252,212,0,0.06)}
    .svc h3{margin:0 0 8px;color:#fff}
    .svc p{margin:0;color:var(--muted);font-size:0.9rem}

    /* Gallery */
    .grid{display:grid;gap:12px;grid-template-columns:repeat(auto-fit,minmax(160px,1fr))}
    .card-img{border-radius:10px;overflow:hidden;background:var(--panel);border:1px solid rgba(255,255,255,0.03);transition:transform .22s ease;position:relative}
    .card-img img{width:100%;height:150px;object-fit:cover;display:block;touch-action:manipulation}
    .card-img:hover{transform:translateY(-8px);box-shadow:0 22px 60px rgba(252,212,0,0.06)}
    .img-title{padding:10px 10px 6px;font-weight:800;color:var(--neon);text-align:center}
    .img-desc{padding:0 12px 12px;color:var(--muted);font-size:0.88rem;text-align:justify}
    .img-badge{position:absolute;left:8px;top:8px;background:rgba(0,0,0,0.5);padding:6px 8px;border-radius:8px;color:var(--neon);font-weight:800;font-size:0.78rem}

    /* Modal / Lightbox */
    .lightbox{
      position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(0,0,0,0.88);z-index:1000;padding:18px;
    }
    .lightbox.open{display:flex}
    .lightbox .inner{max-width:1200px;max-height:90vh;width:100%;display:flex;flex-direction:column;align-items:center;gap:12px}
    .lightbox img{max-width:100%;max-height:84vh;border-radius:10px;box-shadow:0 30px 100px rgba(0,0,0,0.6)}
    .lightbox .controls{display:flex;gap:10px;align-items:center}
    .lightbox .controls button{background:var(--neon);border:none;padding:10px 12px;border-radius:10px;font-weight:900;cursor:pointer}
    .lightbox .caption{color:var(--neon);font-weight:800;margin-top:6px;text-align:center}
    .lightbox .extlink{color:var(--neon);text-decoration:none;font-weight:700;font-size:0.9rem}

    /* Nosotros */
    .nv{display:grid;gap:12px;grid-template-columns:repeat(auto-fit,minmax(220px,1fr))}
    .nv .card-small{padding:12px;border-radius:10px;background:linear-gradient(90deg, rgba(252,212,0,0.03), rgba(255,255,255,0.01));border:1px solid rgba(255,255,255,0.03);color:#fff}

    /* Contact */
    .contact-grid{display:grid;gap:12px}
    @media(min-width:860px){.contact-grid{grid-template-columns:1fr 360px}}
    .btn{display:inline-block;background:var(--neon);color:#060606;padding:10px 14px;border-radius:12px;text-decoration:none;font-weight:900;box-shadow:0 14px 40px rgba(252,212,0,0.08)}

    footer{color:var(--muted);text-align:center;padding:22px 14px;margin-top:18px;border-top:1px solid rgba(255,255,255,0.02)}

    /* WhatsApp icon official style */
    .wa{
      position:fixed;right:14px;bottom:16px;width:68px;height:68px;border-radius:50%;background:linear-gradient(180deg,#28b463,#25d366);color:#fff;display:flex;align-items:center;justify-content:center;font-size:30px;z-index:900;
      box-shadow: 0 20px 60px rgba(37,211,102,0.18);text-decoration:none;font-weight:900;border:3px solid rgba(255,255,255,0.06)
    }

    /* Responsive */
    @media(max-width:880px){
      .menu{display:none}
      .hamburger{display:flex}
      .big-name{font-size:1.18rem}
    }

    /* reveal animation */
    .reveal{opacity:0;transform:translateY(12px);transition:all .6s cubic-bezier(.2,.9,.2,1)}
    .reveal.show{opacity:1;transform:none}
  </style>
</head>
<body>

  <div class="bg-anim" aria-hidden="true"></div>

  <!-- NAV -->
  <div class="nav-wrap">
    <div class="nav" role="navigation" aria-label="Main navigation">
      <div class="brand">
        <div class="logo" aria-hidden="true">T</div>
        <div>
          <div class="title">Logísticas y Suministros Tangram S.A.S</div>
          <div class="sub">Mantenimiento de maquinaria amarilla</div>
        </div>
      </div>

      <!-- desktop menu -->
      <div class="menu" role="menubar" aria-label="Menu principal">
        <a href="#inicio" role="menuitem">🏠 Inicio</a>
        <a href="#servicios" role="menuitem">🧰 Servicios</a>
        <a href="#potencia" role="menuitem">⚙️ Potencia en acción</a>
        <a href="#nosotros" role="menuitem">🏢 Nosotros</a>
        <a href="#contacto" role="menuitem">📞 Contacto</a>
      </div>

      <!-- hamburger (mobile) -->
      <div class="hamburger" id="hamb" aria-label="Abrir menú">
        <span></span><span></span><span></span>
      </div>
    </div>
  </div>

  <!-- RIGHT DRAWER -->
  <div id="drawer" class="drawer" aria-hidden="true">
    <div class="close" id="closeDrawer">✕</div>
    <nav style="display:flex;flex-direction:column;gap:6px;margin-top:6px">
      <a href="#inicio">🏠 Inicio</a>
      <a href="#servicios">🧰 Servicios</a>
      <a href="#potencia">⚙️ Potencia en acción</a>
      <a href="#nosotros">🏢 Nosotros</a>
      <a href="#contacto">📞 Contacto</a>
    </nav>
    <div style="margin-top:auto;padding-top:10px;border-top:1px solid rgba(255,255,255,0.02)">
      <div style="font-weight:800;color:var(--neon);margin-bottom:6px">Contacto rápido</div>
      <a href="https://wa.me/573112913150" style="color:var(--neon);text-decoration:none;font-weight:700">💬 WhatsApp: +57 311 291 3150</a>
      <div style="height:10px"></div>
      <a href="mailto:logisticas.tangram@gmail.com" style="color:var(--neon);text-decoration:none;font-weight:700">✉️ logisticas.tangram@gmail.com</a>
    </div>
  </div>

  <!-- HERO -->
  <header id="inicio" class="hero">
    <div class="big-name reveal"><span class="glow">Logísticas y Suministros</span><br><span style="font-size:0.86rem">Tangram S.A.S</span></div>
    <p class="reveal" style="transition-delay:.06s">Mantenemos tu maquinaria al <strong style="color:var(--neon)">100%</strong> — servicio integral en mantenimiento y repuestos para maquinaria amarilla. Sora & Tunja.</p>
    <div class="badge reveal" style="transition-delay:.12s">Atención rápida • Repuestos • Asesoría técnica</div>
  </header>

  <main>
    <!-- MINI CONTACT -->
    <section class="card reveal" style="transition-delay:.14s">
      <div style="display:flex;justify-content:space-between;gap:12px;align-items:center;flex-wrap:wrap">
        <div>
          <h2>Ubicación</h2>
          <p class="lead">📍 <strong>Sede principal:</strong> Carrera 3-5 #04, Sora, Boyacá<br>🏢 <strong>Oficina alterna:</strong> Plaza Real, Oficina 213, Tunja</p>
        </div>
        <div style="text-align:right">
          <div style="margin-bottom:8px"><a class="btn" href="https://wa.me/573112913150" target="_blank">💬 WhatsApp</a></div>
          <div style="color:var(--muted);margin-top:8px;font-size:0.86rem">Tel: +57 311 291 3150</div>
        </div>
      </div>
    </section>

    <!-- SERVICES -->
    <section id="servicios" class="card reveal" style="transition-delay:.18s">
      <h2>Servicios</h2>
      <p class="lead">Brindamos servicios técnicos especializados para maquinaria amarilla y equipos pesados. Atención para flotas municipales, constructoras y propietarios privados.</p>

      <div class="services" style="margin-top:12px">
        <div class="svc">
          <h3>🔁 Mantenimiento preventivo</h3>
          <p>Planes periódicos, inspecciones, cambio de fluidos y detección temprana de fallas.</p>
        </div>
        <div class="svc">
          <h3>🔧 Mantenimiento correctivo</h3>
          <p>Diagnóstico, rectificación, reconstrucción de conjuntos y reparación integral.</p>
        </div>
        <div class="svc">
          <h3>🛠 Hidráulica y cilindros</h3>
          <p>Reparación de bombas, cilindros y sellos, pruebas de presión y hermeticidad.</p>
        </div>
        <div class="svc">
          <h3>⚙️ Motores y transmisiones</h3>
          <p>Rectificación, sincronización, balanceo y pruebas en banco.</p>
        </div>
        <div class="svc">
          <h3>🔩 Soldadura estructural</h3>
          <p>Restauración de chasis, carrocería y refuerzo estructural.</p>
        </div>
        <div class="svc">
          <h3>📦 Repuestos y suministros</h3>
          <p>Gestión y suministro de piezas con control de calidad y garantía.</p>
        </div>
      </div>
    </section>

    <!-- POTENCIA EN ACCION -->
    <section id="potencia" class="card reveal" style="transition-delay:.22s">
      <h2>Potencia en acción ⚙️</h2>
      <p class="lead">Evidencias de trabajos realizados. Toca una foto para verla en tamaño completo (desliza para ver otras).</p>

      <div class="grid" style="margin-top:12px">
        <!-- items use data attributes for modal -->
        <div class="reveal" style="transition-delay:.12s">
          <div class="card-img">
            <span class="img-badge">1</span>
            <img data-src="https://i.ibb.co/XxpLTctX/IMG-20250909-WA0005.jpg" alt="Bloque del motor">
          </div>
          <div class="img-title">Bloque del motor</div>
          <div class="img-desc">Rectificación y limpieza integral del bloque motor de maquinaria pesada para restablecer compresión y duración.</div>
        </div>

        <div class="reveal" style="transition-delay:.14s">
          <div class="card-img">
            <span class="img-badge">2</span>
            <img data-src="https://i.ibb.co/zW8pdRvB/IMG-20250909-WA0006.jpg" alt="Reparación de carrocería">
          </div>
          <div class="img-title">Reparación de carrocería</div>
          <div class="img-desc">Soldadura estructural y restauración de superficies para prolongar la vida útil del equipo.</div>
        </div>

        <div class="reveal" style="transition-delay:.16s">
          <div class="card-img">
            <span class="img-badge">3</span>
            <img data-src="https://i.ibb.co/QvMtKvFG/IMG-20250909-WA0033.jpg" alt="Toyota revisión preventiva">
          </div>
          <div class="img-title">Toyota revisión preventiva</div>
          <div class="img-desc">Chequeo integral de sistemas hidráulicos y mecánicos en vehículo tipo Toyota de apoyo operativo.</div>
        </div>

        <div class="reveal" style="transition-delay:.18s">
          <div class="card-img">
            <span class="img-badge">4</span>
            <img data-src="https://i.ibb.co/CkqYjGR/IMG-20250909-WA0034.jpg" alt="Bajando motor para reparar">
          </div>
          <div class="img-title">Bajando motor para reparar</div>
          <div class="img-desc">Desmontaje controlado para diagnóstico y reparación integral del conjunto motor-transmisión.</div>
        </div>

        <div class="reveal" style="transition-delay:.20s">
          <div class="card-img">
            <span class="img-badge">5</span>
            <img data-src="https://i.ibb.co/kVZmx7X4/IMG-20250909-WA0040.jpg" alt="Mantenimiento preventivo">
          </div>
          <div class="img-title">Mantenimiento preventivo</div>
          <div class="img-desc">Rutinas de inspección planificadas para evitar fallas y optimizar tiempos de operación.</div>
        </div>

        <div class="reveal" style="transition-delay:.22s">
          <div class="card-img">
            <span class="img-badge">6</span>
            <img data-src="https://i.ibb.co/tTf6ZCmJ/IMG-20250909-WA0041.jpg" alt="Cambio de aceite">
          </div>
          <div class="img-title">Cambio de aceite</div>
          <div class="img-desc">Reemplazo de aceite y filtros con gestión responsable de residuos y control de calidad.</div>
        </div>

        <div class="reveal" style="transition-delay:.24s">
          <div class="card-img">
            <span class="img-badge">7</span>
            <img data-src="https://i.ibb.co/mV2phyHK/IMG-20250909-WA0037.jpg" alt="Cilindro compactador">
          </div>
          <div class="img-title">Cilindro compactador</div>
          <div class="img-desc">Mantenimiento y ajuste de cilindros compactadores para garantizar uniformidad en trabajos de compactación.</div>
        </div>

        <div class="reveal" style="transition-delay:.26s">
          <div class="card-img">
            <span class="img-badge">8</span>
            <img data-src="https://i.ibb.co/Mxm5nr15/IMG-20250909-WA0012.jpg" alt="Culata del motor">
          </div>
          <div class="img-title">Culata del motor</div>
          <div class="img-desc">Reparación y calibración de culatas con pruebas de estanqueidad y ajuste de válvulas.</div>
        </div>

        <div class="reveal" style="transition-delay:.28s">
          <div class="card-img">
            <span class="img-badge">9</span>
            <img data-src="https://i.ibb.co/5XP7BQdC/IMG-20250909-WA0035.jpg" alt="Articulación de cilindro hidráulico">
          </div>
          <div class="img-title">Articulación de cilindro hidráulico</div>
          <div class="img-desc">Ajuste y reemplazo de juntas y componentes para evitar fugas y pérdida de fuerza.</div>
        </div>

        <div class="reveal" style="transition-delay:.30s">
          <div class="card-img">
            <span class="img-badge">10</span>
            <img data-src="https://i.ibb.co/ZpH70Fr5/IMG-20250909-WA0032.jpg" alt="Cambio de rodamientos">
          </div>
          <div class="img-title">Cambio de rodamientos</div>
          <div class="img-desc">Sustitución de rodamientos, alineación y lubricación para garantizar operación segura.</div>
        </div>
      </div>
    </section>

    <!-- NOSOTROS -->
    <section id="nosotros" class="card reveal" style="transition-delay:.34s">
      <h2>Nosotros</h2>

      <div class="nv" style="margin-top:12px">
        <div class="card-small">
          <h3>MISIÓN</h3>
          <p class="lead">La empresa tiene como propósito brindar un acompañamiento técnico, preciso y confiable a entidades públicas, privadas y mixtas, así como a municipios interesados en fortalecer sus operaciones. Su labor se orienta a mejorar los niveles sociales, ambientales y económicos mediante el mantenimiento especializado de maquinaria amarilla. Para ello, integra conocimientos, experiencia del personal y optimiza recursos y esfuerzos, generando un impacto positivo en el desarrollo comunitario.</p>
        </div>

        <div class="card-small">
          <h3>VISIÓN</h3>
          <p class="lead">Con principios de cumplimiento, transparencia, compromiso y ética profesional, la organización busca consolidarse como líder en el mantenimiento de maquinaria amarilla. Su meta es alcanzar, para el año 2030, un reconocimiento destacado en los ámbitos departamental y nacional, optimizando el uso de los recursos disponibles para elevar la eficiencia operativa de sus aliados y contribuir significativamente al bienestar general de la sociedad.</p>
        </div>
      </div>

      <div style="margin-top:12px" class="row">
        <div style="flex:1;min-width:220px">
          <h3>Valores</h3>
          <ul style="color:var(--muted);padding-left:18px;line-height:1.6">
            <li>Compromiso y cumplimiento</li>
            <li>Transparencia y ética profesional</li>
            <li>Seguridad en el trabajo</li>
            <li>Respeto por el medio ambiente</li>
          </ul>
        </div>
        <div style="flex:1;min-width:220px">
          <h3>Clientes / Sectores</h3>
          <p class="lead">Entidades públicas, municipios, empresas de construcción y agricultura, contratistas y flotas de maquinaria.</p>
        </div>
      </div>
    </section>

    <!-- CONTACTO -->
    <section id="contacto" class="card reveal" style="transition-delay:.38s">
      <h2>Contacto</h2>
      <div class="contact-grid">
        <div>
          <p class="lead">Para cotizaciones, emergencias o asesoría técnica, comunícate con nosotros. Indica tipo de maquinaria, servicio y teléfono.</p>
          <p><strong>Sede principal:</strong> Carrera 3-5 #04, Sora, Boyacá</p>
          <p><strong>Oficina alterna:</strong> Plaza Real, Oficina 213, Tunja</p>
          <p><strong>Tel / WhatsApp:</strong> <a href="https://wa.me/573112913150" style="color:var(--neon);text-decoration:none">+57 311 291 3150</a></p>
          <p><strong>Correo:</strong> <a href="mailto:logisticas.tangram@gmail.com" style="color:var(--neon);text-decoration:none">logisticas.tangram@gmail.com</a></p>
          <div style="margin-top:10px">
            <a class="btn" href="https://wa.me/573112913150" target="_blank">Contactar por WhatsApp</a>
          </div>
        </div>

        <div style="background:rgba(255,255,255,0.02);padding:12px;border-radius:10px">
          <h3>Solicitar cotización</h3>
          <form action="mailto:logisticas.tangram@gmail.com" method="post" enctype="text/plain" style="display:flex;flex-direction:column;gap:8px;margin-top:8px">
            <input name="Nombre" placeholder="Nombre / Empresa" style="padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:#fff" required>
            <input name="Telefono" placeholder="Teléfono" style="padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:#fff" required>
            <input name="Maquinaria" placeholder="Tipo de maquinaria" style="padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:#fff">
            <textarea name="Detalle" placeholder="Breve detalle del servicio" rows="3" style="padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:#fff"></textarea>
            <button class="btn" type="submit">Enviar solicitud</button>
          </form>
        </div>
      </div>
    </section>
  </main>

  <footer>
    © 2025 Logísticas y Suministros Tangram S.A.S — Carrera 3-5 #04, Sora — Oficina: Plaza Real 213, Tunja — <a href="mailto:logisticas.tangram@gmail.com" style="color:var(--neon);text-decoration:none">logisticas.tangram@gmail.com</a>
  </footer>

  <!-- LIGHTBOX / MODAL -->
  <div id="lightbox" class="lightbox" aria-hidden="true">
    <div class="inner">
      <img id="lightboxImg" src="" alt="">
      <div class="caption" id="lightboxCaption"></div>
      <div class="controls">
        <button id="prevBtn">◀</button>
        <a id="extLink" class="extlink" href="#" target="_blank" rel="noopener">Abrir original</a>
        <button id="nextBtn">▶</button>
        <button id="closeBtn" style="background:rgba(0,0,0,0.6);color:var(--neon);">Cerrar ✕</button>
      </div>
    </div>
  </div>

  <!-- WHATSAPP ICON (official-like) -->
  <a class="wa" href="https://wa.me/573112913150" target="_blank" aria-label="WhatsApp">💬</a>

  <script>
    // mobile drawer toggle
    const hamb = document.getElementById('hamb');
    const drawer = document.getElementById('drawer');
    const closeDrawer = document.getElementById('closeDrawer');
    hamb && hamb.addEventListener('click', () => {
      drawer.classList.add('open'); drawer.setAttribute('aria-hidden','false'); document.body.style.overflow='hidden';
    });
    closeDrawer && closeDrawer.addEventListener('click', () => {
      drawer.classList.remove('open'); drawer.setAttribute('aria-hidden','true'); document.body.style.overflow='';
    });
    drawer.querySelectorAll('a').forEach(a=>a.addEventListener('click',()=>{drawer.classList.remove('open');drawer.setAttribute('aria-hidden','true');document.body.style.overflow='';}));

    // smooth scroll for anchors
    document.querySelectorAll('a[href^="#"]').forEach(a=>{
      a.addEventListener('click', function(e){
        const href = this.getAttribute('href');
        if(href.length>1 && document.querySelector(href)){
          e.preventDefault();
          document.querySelector(href).scrollIntoView({behavior:'smooth',block:'start'});
        }
      });
    });

    // highlight menu active
    const sections = Array.from(document.querySelectorAll('main section, header.hero'));
    const desktopLinks = Array.from(document.querySelectorAll('.menu a'));
    function onScroll(){
      const y = window.scrollY + 160;
      let current = sections[0].id || 'inicio';
      for(const s of sections){
        if(s.offsetTop <= y) current = s.id || current;
      }
      desktopLinks.forEach(a => {
        const href = a.getAttribute('href').replace('#','');
        if(href === current) a.classList.add('active'); else a.classList.remove('active');
      });
    }
    window.addEventListener('scroll', onScroll);
    onScroll();

    // reveal animation for elements (.reveal)
    const observer = new IntersectionObserver((entries)=>{
      entries.forEach(e=>{
        if(e.isIntersecting){ e.target.classList.add('show'); observer.unobserve(e.target); }
      });
    },{threshold:0.12});
    document.querySelectorAll('.reveal').forEach(el=>observer.observe(el));
    // show big name after load
    window.addEventListener('load', ()=>{ document.querySelector('.big-name')?.classList.add('show'); });

    // GALLERY LIGHTBOX (zoom on touch)
    const imgs = Array.from(document.querySelectorAll('.card-img img'));
    const lightbox = document.getElementById('lightbox');
    const lightboxImg = document.getElementById('lightboxImg');
    const caption = document.getElementById('lightboxCaption');
    const extLink = document.getElementById('extLink');
    const prevBtn = document.getElementById('prevBtn');
    const nextBtn = document.getElementById('nextBtn');
    const closeBtn = document.getElementById('closeBtn');

    // build array of images and captions and original imgbb links
    const gallery = imgs.map((img, i) => {
      const src = img.getAttribute('data-src') || img.src;
      const alt = img.getAttribute('alt') || '';
      // map known imgbb hosts to the view page (fallback)
      const imgbbPage = src.includes('i.ibb.co') ? src.replace('i.ibb.co','ibb.co').replace('/','/').replace('.jpg','.jpg') : src;
      return {src, alt, page: imgbbPage};
    });

    // lazy-set image src for thumbnails (improve performance)
    imgs.forEach(img => {
      const s = img.getAttribute('data-src');
      if(s) img.src = s;
    });

    let currentIndex = 0;
    function openLightbox(index){
      const it = gallery[index];
      currentIndex = index;
      lightboxImg.src = it.src;
      caption.textContent = it.alt;
      extLink.href = it.page;
      lightbox.classList.add('open'); lightbox.setAttribute('aria-hidden','false'); document.body.style.overflow='hidden';
    }
    function closeLightbox(){
      lightbox.classList.remove('open'); lightbox.setAttribute('aria-hidden','true'); document.body.style.overflow='';
      lightboxImg.src = '';
    }
    function nextImage(){
      currentIndex = (currentIndex+1) % gallery.length;
      openLightbox(currentIndex);
    }
    function prevImage(){
      currentIndex = (currentIndex-1 + gallery.length) % gallery.length;
      openLightbox(currentIndex);
    }

    imgs.forEach((img, idx) => {
      img.addEventListener('click', ()=> openLightbox(idx));
      img.addEventListener('keypress', (e)=>{ if(e.key==='Enter') openLightbox(idx); });
    });

    nextBtn?.addEventListener('click', nextImage);
    prevBtn?.addEventListener('click', prevImage);
    closeBtn?.addEventListener('click', closeLightbox);

    // close lightbox on background click
    lightbox.addEventListener('click', (e) => {
      if(e.target === lightbox) closeLightbox();
    });

    // keyboard navigation
    document.addEventListener('keydown', (e) => {
      if(lightbox.classList.contains('open')){
        if(e.key === 'ArrowRight') nextImage();
        if(e.key === 'ArrowLeft') prevImage();
        if(e.key === 'Escape') closeLightbox();
      }
    });

    // close drawer if click outside (on mobile)
    document.addEventListener('click', (ev) => {
      const drawerEl = document.getElementById('drawer');
      if(drawerEl && drawerEl.classList.contains('open') && !drawerEl.contains(ev.target) && !ev.target.closest('.hamburger')){
        drawerEl.classList.remove('open'); drawerEl.setAttribute('aria-hidden','true'); document.body.style.overflow='';
      }
    });
  </script>
</body>
	</html>

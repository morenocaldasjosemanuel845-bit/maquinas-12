<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Examen interactivo | Máquinas Eléctricas y Subestaciones</title>
  <style>
    :root{
      --green-900:#063b22;
      --green-800:#07542e;
      --green-700:#0b6b3a;
      --green-600:#168246;
      --green-100:#eaf6ee;
      --green-050:#f5fbf7;
      --ink:#1d2b24;
      --muted:#60736a;
      --line:#c7dfd0;
      --danger:#b91c1c;
      --ok:#047857;
      --warn:#b45309;
      --white:#ffffff;
      --shadow:0 12px 30px rgba(2, 42, 23, .12);
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family:Inter, Segoe UI, Arial, sans-serif;
      color:var(--ink);
      background:linear-gradient(135deg,#f7fbf8 0%,#edf7f0 45%,#ffffff 100%);
    }
    header{
      background:linear-gradient(135deg,var(--green-900),var(--green-700));
      color:white;
      padding:28px 22px 24px;
      border-bottom:6px solid #9fd2aa;
      position:sticky;
      top:0;
      z-index:20;
      box-shadow:0 8px 20px rgba(0,0,0,.18);
    }
    .header-wrap{max-width:1180px;margin:auto;display:grid;grid-template-columns:1fr auto;gap:18px;align-items:center}
    h1{font-size:clamp(26px,4vw,46px);margin:0 0 8px;font-weight:900;letter-spacing:.3px}
    .subtitle{font-size:clamp(14px,2vw,18px);opacity:.95;line-height:1.4}
    .badge{display:inline-flex;gap:8px;align-items:center;background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.3);padding:8px 12px;border-radius:999px;font-weight:700;margin-top:12px}
    .score-card{background:white;color:var(--green-900);border-radius:22px;padding:14px 18px;min-width:230px;text-align:center;box-shadow:var(--shadow)}
    .score-card .label{font-size:12px;text-transform:uppercase;letter-spacing:.08em;color:var(--muted);font-weight:800}
    .score-card .score{font-size:34px;font-weight:900;margin:4px 0;color:var(--green-800)}
    main{max-width:1180px;margin:24px auto;padding:0 18px 80px}
    .panel{background:white;border:1px solid var(--line);border-radius:24px;padding:20px;margin:18px 0;box-shadow:var(--shadow)}
    .intro-grid{display:grid;grid-template-columns:1.2fr .8fr;gap:18px}
    h2{margin:0 0 12px;color:var(--green-900);font-size:28px}
    h3{margin:0;color:var(--green-900)}
    p{line-height:1.55}
    .pillbar{display:flex;gap:10px;flex-wrap:wrap;margin-top:14px}
    .pill{background:var(--green-100);border:1px solid var(--line);color:var(--green-900);border-radius:999px;padding:8px 12px;font-weight:700;font-size:14px}
    .controls{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-top:14px}
    button{border:0;border-radius:16px;padding:12px 14px;font-weight:800;cursor:pointer;transition:.2s;letter-spacing:.1px}
    button.primary{background:var(--green-700);color:white}
    button.secondary{background:var(--green-100);color:var(--green-900);border:1px solid var(--line)}
    button.warning{background:#fff7ed;color:var(--warn);border:1px solid #fed7aa}
    button:hover{transform:translateY(-1px);filter:brightness(.98)}
    .progress-wrap{height:14px;background:#dfeee5;border-radius:999px;overflow:hidden;margin-top:14px;border:1px solid var(--line)}
    .progress{height:100%;width:0;background:linear-gradient(90deg,var(--green-600),#46b86a);transition:width .3s}
    .legend{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;margin-top:12px;color:var(--muted);font-size:13px}
    .section-title{display:flex;align-items:center;gap:12px;margin:28px 0 14px}
    .section-title span{display:grid;place-items:center;background:var(--green-800);color:white;border-radius:14px;width:44px;height:44px;font-weight:900}
    .section-title h2{margin:0}
    .question{background:white;border:1px solid var(--line);border-radius:22px;margin:14px 0;padding:18px;box-shadow:0 8px 20px rgba(0,0,0,.05)}
    .q-head{display:flex;gap:12px;align-items:flex-start;margin-bottom:12px}
    .q-num{flex:0 0 36px;height:36px;border-radius:12px;background:var(--green-800);color:white;display:grid;place-items:center;font-weight:900}
    .q-meta{font-size:12px;color:var(--green-800);font-weight:900;text-transform:uppercase;letter-spacing:.08em;margin-bottom:4px}
    .q-text{font-size:18px;font-weight:800;line-height:1.35;color:#173b28}
    .options{display:grid;gap:9px;margin-top:12px}
    label.option{display:flex;gap:10px;align-items:flex-start;padding:12px;border:1px solid var(--line);border-radius:14px;background:var(--green-050);cursor:pointer;line-height:1.4}
    label.option:hover{border-color:#73b987;background:#f0faf3}
    input[type="radio"], input[type="checkbox"]{margin-top:3px;accent-color:var(--green-700);transform:scale(1.1)}
    input[type="text"], textarea, select{width:100%;border:1px solid var(--line);border-radius:14px;padding:12px 14px;font:inherit;outline:none;background:#fcfffd}
    input[type="text"]:focus, textarea:focus, select:focus{border-color:var(--green-600);box-shadow:0 0 0 3px rgba(22,130,70,.12)}
    .match-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-top:12px}
    .match-row{display:grid;grid-template-columns:1fr 1.1fr;gap:10px;align-items:center;padding:10px;border:1px dashed var(--line);border-radius:14px;background:#fbfffc}
    .feedback{display:none;margin-top:12px;padding:12px;border-radius:14px;font-weight:700;line-height:1.45}
    .feedback.ok{display:block;background:#e7f8ed;color:var(--ok);border:1px solid #a7e4ba}
    .feedback.bad{display:block;background:#fff1f2;color:var(--danger);border:1px solid #fecdd3}
    .feedback.neutral{display:block;background:#eff6ff;color:#1d4ed8;border:1px solid #bfdbfe}
    .explain{font-weight:500;color:#244535;margin-top:6px}
    .tag{display:inline-flex;align-items:center;background:#ecfdf3;color:var(--green-800);border:1px solid var(--line);padding:3px 8px;border-radius:999px;font-size:12px;font-weight:800;margin-right:6px}
    .two-col{display:grid;grid-template-columns:1fr 1fr;gap:12px}
    .formula{font-family:Georgia,serif;background:#f4fbf6;border:1px solid var(--line);padding:10px 12px;border-radius:12px;font-size:18px;text-align:center;color:var(--green-900);margin:8px 0}
    .small{font-size:13px;color:var(--muted)}
    .results{display:none;background:linear-gradient(135deg,#ffffff,#eef9f1);border:2px solid var(--green-600);border-radius:24px;padding:22px;box-shadow:var(--shadow);margin-top:20px}
    .results.show{display:block}
    .result-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-top:12px}
    .metric{background:white;border:1px solid var(--line);border-radius:18px;padding:14px;text-align:center}
    .metric b{font-size:28px;color:var(--green-800)}
    .study-tip{background:#063b22;color:white;border-radius:18px;padding:16px;margin-top:14px;line-height:1.5}
    .footer-actions{position:sticky;bottom:0;background:rgba(255,255,255,.92);backdrop-filter:blur(10px);border-top:1px solid var(--line);padding:12px 18px;z-index:10}
    .footer-inner{max-width:1180px;margin:auto;display:flex;gap:12px;justify-content:flex-end;flex-wrap:wrap}
    @media(max-width:900px){.header-wrap,.intro-grid,.two-col,.match-grid{grid-template-columns:1fr}.controls,.legend,.result-grid{grid-template-columns:1fr 1fr}.score-card{min-width:unset}.match-row{grid-template-columns:1fr}}
    @media(max-width:560px){.controls,.legend,.result-grid{grid-template-columns:1fr}.q-text{font-size:16px}header{position:relative}}
    @media print{header,.footer-actions,.controls button,.no-print{display:none!important}body{background:white}.panel,.question{box-shadow:none;break-inside:avoid}.feedback{display:block}.results{display:block}}
  </style>
</head>
<body>
<header>
  <div class="header-wrap">
    <div>
      <h1>Examen interactivo: Máquinas Eléctricas y Subestaciones</h1>
      <div class="subtitle">Evaluación mixta con preguntas para marcar, completar, relacionar y resolver. Incluye teoría de los 4 PDF: subestaciones, sobretensiones, simbología, redes primarias, aparamenta y transformadores de medida.</div>
      <div class="badge">🟢 Modalidad: práctica + repaso de respuestas clave</div>
    </div>
    <div class="score-card" aria-live="polite">
      <div class="label">Puntaje actual</div>
      <div class="score"><span id="scoreNow">0</span>/<span id="scoreTotal">0</span></div>
      <div class="small" id="scoreText">Responde y presiona “Calificar”.</div>
    </div>
  </div>
</header>

<main>
  <section class="panel intro-grid">
    <div>
      <h2>Indicaciones</h2>
      <p>Este examen está diseñado para estudiar de forma activa. Algunas preguntas tienen una sola respuesta, otras admiten varias, otras se completan con palabras clave y otras relacionan conceptos. Lee con cuidado porque el examen está mezclado.</p>
      <div class="pillbar">
        <span class="pill">✅ Marcar alternativa</span>
        <span class="pill">✍️ Completar</span>
        <span class="pill">🔗 Relacionar</span>
        <span class="pill">🧮 Fórmulas</span>
        <span class="pill">🎯 Retroalimentación</span>
      </div>
      <div class="progress-wrap"><div class="progress" id="progressBar"></div></div>
      <div class="legend">
        <span>PDF 1: subestaciones y pararrayos</span>
        <span>PDF 2: símbolos, redes y aisladores</span>
        <span>PDF 3: red primaria</span>
        <span>PDF 4: componentes y TT/TC</span>
      </div>
    </div>
    <div>
      <h2>Modo de uso</h2>
      <p><b>1.</b> Responde todo el examen.<br><b>2.</b> Presiona <b>Calificar examen</b>.<br><b>3.</b> Revisa la explicación de cada pregunta.<br><b>4.</b> Reinicia y repite hasta superar 90%.</p>
      <div class="controls">
        <button class="primary" onclick="gradeExam()">Calificar examen</button>
        <button class="secondary" onclick="showAnswers()">Mostrar respuestas</button>
        <button class="warning" onclick="resetExam()">Reiniciar</button>
        <button class="secondary" onclick="window.print()">Imprimir / PDF</button>
      </div>
    </div>
  </section>

  <div id="exam"></div>

  <section class="results" id="resultsBox">
    <h2>Resultado general</h2>
    <p id="resultMessage"></p>
    <div class="result-grid">
      <div class="metric"><span>Correctas</span><br><b id="correctCount">0</b></div>
      <div class="metric"><span>Incorrectas</span><br><b id="wrongCount">0</b></div>
      <div class="metric"><span>Porcentaje</span><br><b id="percentScore">0%</b></div>
      <div class="metric"><span>Nivel</span><br><b id="levelText">-</b></div>
    </div>
    <div class="study-tip" id="studyTip"></div>
  </section>
</main>

<div class="footer-actions no-print">
  <div class="footer-inner">
    <button class="secondary" onclick="scrollToTop()">Subir</button>
    <button class="primary" onclick="gradeExam()">Calificar examen</button>
    <button class="warning" onclick="resetExam()">Reiniciar</button>
  </div>
</div>

<script>
const sections = [
  {
    title:"PDF 1 · Subestaciones, sobretensiones y pararrayos",
    icon:"⚡",
    questions:[
      {type:"single", topic:"Subestaciones", q:"¿Qué es una subestación de distribución?", options:["Un tablero que solo mide energía en baja tensión.","Un conjunto de instalaciones, equipos y obras civiles que transforma niveles de tensión, realiza maniobra, protección, medición y entrega energía.","Un conductor utilizado únicamente para redes aéreas.","Un dispositivo que solo protege contra descargas atmosféricas."], answer:1, explain:"Una subestación integra transformación, seccionamiento, protección, medición y distribución. No es solo el transformador."},
      {type:"multi", topic:"Criterios", q:"Selecciona las consideraciones principales para el diseño de subestaciones.", options:["Confiabilidad","Flexibilidad","Seguridad","Color del gabinete como criterio principal","Continuidad y calidad del servicio"], answer:[0,1,2,4], explain:"El diseño debe asegurar operación confiable, flexible y segura, manteniendo continuidad y calidad del suministro."},
      {type:"single", topic:"Pararrayos", q:"¿Qué es un pararrayos o descargador de sobretensión?", options:["Un dispositivo destinado a limitar sobretensiones y descargar la energía transitoria a tierra.","Un fusible de baja tensión para circuitos domiciliarios.","Un transformador de corriente para relés.","Un aislador que elimina totalmente las fallas."], answer:0, explain:"El pararrayos se conecta entre línea y tierra y protege el aislamiento frente a descargas atmosféricas, maniobras u otras sobretensiones."},
      {type:"multi", topic:"Selección de pararrayos", q:"¿De qué parámetros depende la selección de un pararrayos?", options:["MCOV o Uc","Sobretensión temporal TOV","Tensión nominal Ur","Corriente nominal de descarga In","Color de la porcelana"], answer:[0,1,2,3], explain:"La selección se basa en Uc, TOV, Ur, In y el nivel de protección o tensión residual."},
      {type:"text", topic:"Tensión residual", q:"Completa: La tensión residual Ures del pararrayos es la máxima tensión que aparece en el equipo protegido mientras el pararrayos ________ la sobretensión a ________.", answer:["descarga tierra","descarga a tierra","descarga la sobretensión a tierra"], explain:"Ures es la tensión que queda en bornes del equipo protegido durante la descarga del pararrayos."},
      {type:"single", topic:"Tensión máxima", q:"¿Cuál es la tensión máxima del sistema para una red eléctrica de 22,9 kV?", options:["22,9 kV","23 kV","24 kV","36 kV"], answer:2, explain:"Se usa Um = Vn × 1,05. Para 22,9 kV, el valor normalizado o eficaz usado es aproximadamente 24 kV."},
      {type:"single", topic:"Aislamiento", q:"¿A qué se llama nivel de aislamiento?", options:["A la capacidad de un equipo para soportar sobretensiones sin deteriorarse.","A la corriente nominal del transformador.","A la distancia del poste al suelo.","Al calibre del cable en mm²."], answer:0, explain:"El nivel de aislamiento expresa la aptitud dieléctrica del equipo frente a solicitaciones eléctricas."},
      {type:"single", topic:"Coordinación de aislamiento", q:"¿En qué se basa la coordinación de aislamiento?", options:["Solo en la corriente nominal.","En seleccionar el aislamiento y la protección según pruebas a frecuencia industrial de 60 Hz y sobretensiones tipo rayo.","Solo en el peso del equipo.","En la longitud de la barra de cobre."], answer:1, explain:"La coordinación relaciona el aislamiento de los equipos con las protecciones para soportar sobretensiones internas y externas."},
      {type:"multi", topic:"Sobretensiones temporales", q:"¿Qué fallas pueden ocasionar las sobretensiones temporales?", options:["Fallas a tierra","Pérdidas o rechazo de carga","Deterioro del aislamiento","Envejecimiento prematuro de equipos","Cambio de color del cable"], answer:[0,1,2,3], explain:"Las sobretensiones temporales se asocian a fallas a tierra, pérdida de carga y esfuerzos que deterioran el aislamiento."}
    ]
  },
  {
    title:"PDF 2 · Simbología, esquemas, sistemas de distribución y aisladores",
    icon:"📐",
    questions:[
      {type:"multi", topic:"Simbología", q:"Marca las ventajas del uso de símbolos electrotécnicos.", options:["Uso universal","Ahorro de tiempo en la representación de circuitos","Facilitan interpretar circuitos complejos","Permiten comunicación técnica independiente del idioma","Eliminan la necesidad de estudiar normas"], answer:[0,1,2,3], explain:"Los símbolos normalizados simplifican la comunicación técnica y la lectura de planos."},
      {type:"multi", topic:"Normas", q:"¿Bajo qué normas o referencias se representa la simbología eléctrica?", options:["IEC","CNE","ANSI","NEMA","Normas inventadas por cada técnico"], answer:[0,1,2,3], explain:"La representación puede basarse en IEC, CNE, ANSI, NEMA y otras normas técnicas aplicables."},
      {type:"multi", topic:"Plano de recorrido MT", q:"¿Qué debe contener el esquema o plano de recorrido de una red de media tensión?", options:["Recorrido del alimentador","Cortes y detalles de calles o avenidas que cruza","Detalles de buzones, si existen","Ubicación y detalle del sistema de puesta a tierra","Decoración comercial del plano"], answer:[0,1,2,3], explain:"El plano de recorrido documenta el trazado físico, cruces, buzones y puesta a tierra."},
      {type:"multi", topic:"Red de distribución", q:"¿Qué aspectos se deben considerar para realizar una red de distribución?", options:["Seguridad del suministro","Caída de tensión","Sistema de protección","Planeamiento","Solo el precio del conductor"], answer:[0,1,2,3], explain:"El diseño debe cuidar continuidad, niveles de tensión, protección y crecimiento de la demanda."},
      {type:"single", topic:"Sistema radial", q:"¿Qué es un esquema de distribución radial?", options:["Circuito donde los alimentadores parten de una subestación o punto de alimentación y se alejan sin retornar al origen.","Circuito cerrado que regresa siempre al punto de origen.","Sistema exclusivo de redes subterráneas.","Sistema donde no existen protecciones."], answer:0, explain:"El radial es simple y económico, pero tiene menor respaldo que un anillo."},
      {type:"multi", topic:"Aisladores", q:"¿Cuáles son las causas por las que un aislador podría dejar pasar corriente?", options:["Conductividad de masa","Conductividad superficial","Perforación del aislador","Descarga disruptiva a través del aire","Exceso de pintura verde"], answer:[0,1,2,3], explain:"El aislador puede fallar por conducción interna, superficial, perforación o arco externo por el aire."},
      {type:"multi", topic:"Características de distribución", q:"Menciona características de los sistemas de distribución según el material.", options:["Eficiente sistema de protección","Facilidad de mantenimiento","Facilidad de operación","Baja potencia de cortocircuito","Ausencia total de fallas"], answer:[0,1,2,3], explain:"El material destaca protección, operación, mantenimiento y baja potencia de cortocircuito como rasgos relevantes."},
      {type:"single", topic:"Economía", q:"De los sistemas de distribución, ¿cuál es más económico ejecutarlo?", options:["Sistema aéreo","Sistema subterráneo en ductos múltiples","Sistema encapsulado GIS","Sistema con doble anillo permanente"], answer:0, explain:"El sistema aéreo suele ser más económico de ejecutar por menor obra civil e instalación más simple."},
      {type:"match", topic:"Relacionar conceptos", q:"Relaciona cada concepto con su definición.", pairs:[
        ["Esquema unifilar","Representa conexiones principales con una sola línea"],
        ["Plano de recorrido","Muestra el trazado físico del alimentador"],
        ["Anillo","Permite alimentación alternativa y mayor confiabilidad"],
        ["Aislador","Impide el paso de corriente del conductor a la estructura"]
      ], explain:"Estos conceptos suelen confundirse; el unifilar es eléctrico, el recorrido es físico, el anillo da respaldo y el aislador separa eléctricamente."}
    ]
  },
  {
    title:"PDF 3 · Diseño de red primaria subterránea y aérea",
    icon:"🔌",
    questions:[
      {type:"single", topic:"Caída de tensión", q:"¿Cuál es la máxima caída de tensión permitida en un alimentador de media tensión urbano?", options:["1,5 %","2,0 %","3,5 %","10 %"], answer:2, explain:"Para sistemas urbanos o subestaciones convencionales se toma 3,5 % de Un; para sistemas rurales, 6 %."},
      {type:"multi", topic:"Ampacidad", q:"¿De qué depende la capacidad de corriente de los cables?", options:["Clase de servicio","Disposición de los cables","Resistividad térmica del suelo","Profundidad de tendido","Temperatura del suelo a la profundidad de tendido"], answer:[0,1,2,3,4], explain:"La ampacidad real se corrige por condiciones de instalación, suelo, temperatura y proximidad."},
      {type:"single", topic:"Cable MT", q:"¿Qué tipo de cable se utiliza para redes de distribución primaria de media tensión subterránea?", options:["N2XSY","TW doméstico","UTP categoría 6","Cordón flexible bipolar"], answer:0, explain:"El cable N2XSY es el cable seco empleado en redes de MT, con conductor de cobre, aislamiento XLPE, pantallas y cubierta exterior."},
      {type:"single", topic:"Terminal MT", q:"¿Cuál es el objetivo de los terminales de media tensión?", options:["Eliminar el gradiente de tensión en el extremo del cable y dar continuidad a la pantalla semiconductora.","Aumentar la potencia del transformador.","Reducir la frecuencia de 60 Hz.","Sustituir el sistema de puesta a tierra."], answer:0, explain:"El terminal controla el campo eléctrico en el extremo del cable y asegura continuidad de pantalla."},
      {type:"single", topic:"Tendido", q:"¿Cuál sería la mínima profundidad de tendido para una red subterránea de media tensión?", options:["0,30 m","0,60 m","1,00 m","3,00 m"], answer:2, explain:"Para media tensión subterránea, el material indica 1 m recomendado por CNE Suministro."},
      {type:"single", topic:"Ductos", q:"¿Dónde es necesario usar ductos de concreto?", options:["En cruces de avenidas o lugares con tránsito de maquinaria que pueda afectar el cable.","Dentro del transformador.","Sobre conductores aéreos.","En todos los tableros de baja tensión."], answer:0, explain:"Los ductos dan protección mecánica en cruces, avenidas o zonas con tránsito pesado."},
      {type:"multi", topic:"Terminales", q:"¿Qué especificaciones son necesarias para seleccionar un terminal de media tensión?", options:["Tensión de operación del cable","Calibre del cable","Instalación interior y/o exterior","Nivel de aislamiento","Color del equipo"], answer:[0,1,2,3], explain:"La selección depende de tensión, calibre, tipo de instalación y nivel de aislamiento."},
      {type:"single", topic:"Disposición de cables", q:"¿Cómo afecta la disposición de los cables directamente enterrados?", options:["Afecta la capacidad de corriente según tablas del fabricante.","No afecta nada.","Solo cambia el color de la cubierta.","Elimina la caída de tensión por completo."], answer:0, explain:"La disposición, separación y proximidad afectan la disipación térmica y reducen o aumentan la ampacidad."},
      {type:"single", topic:"Corriente de choque", q:"¿Qué es la corriente de choque?", options:["El máximo valor que puede alcanzar la corriente de cortocircuito cuando ocurre en las peores condiciones.","La corriente normal de iluminación.","La corriente del neutro solamente.","La corriente usada para medir energía mensual."], answer:0, explain:"La corriente de choque es un valor pico asociado al cortocircuito; suele estimarse como Ich ≈ 2,55 Icc."},
      {type:"single", topic:"Red aérea", q:"¿Cuál es el conductor usual en redes aéreas de media tensión indicado en el material?", options:["AAAC, aleación de aluminio","N2XSY enterrado","Cable UTP","Cable mellizo"], answer:0, explain:"En redes aéreas MT se usa AAAC por resistencia mecánica y buena resistencia a la corrosión."},
      {type:"text", topic:"Fórmula", q:"Completa la fórmula de corriente trifásica con potencia aparente: I = S / (_____ × U).", answer:["raiz3","√3","sqrt3","raiz de 3","raíz de 3"], explain:"La corriente trifásica se calcula como I = S/(√3·U)."}
    ]
  },
  {
    title:"PDF 4 · Selección de componentes de la subestación",
    icon:"🧰",
    questions:[
      {type:"single", topic:"Aparamenta", q:"¿A qué se le llama aparamenta de media tensión?", options:["Al conjunto de aparatos o dispositivos para maniobra, control, regulación, seguridad y canalización en instalaciones de media tensión.","A la pintura exterior de la subestación.","A un solo transformador de baja tensión.","A una red de datos."], answer:0, explain:"La aparamenta agrupa dispositivos de maniobra, protección, medida, regulación y control."},
      {type:"multi", topic:"Funciones", q:"¿Qué función cumple la aparamenta en una subestación?", options:["Maniobra o corte","Control","Protección","Regulación","Canalización y seguridad"], answer:[0,1,2,3,4], explain:"La aparamenta permite operar, proteger, controlar, regular y canalizar la energía eléctrica con seguridad."},
      {type:"multi", topic:"Características comunes", q:"¿Cuáles son las características comunes de los aparatos de maniobra?", options:["Tensión asignada","Nivel de aislamiento asignado","Corriente nominal o de servicio continuo","Poder de corte asignado","Valor de cresta del poder de corte asignado"], answer:[0,1,2,3,4], explain:"Estos parámetros se verifican para seleccionar interruptores, seccionadores y demás equipos de MT."},
      {type:"single", topic:"Transformadores de medida", q:"¿Cuáles son los objetivos de los transformadores de medida?", options:["Aislar o separar circuitos, evitar perturbaciones electromagnéticas y obtener corrientes o tensiones proporcionales para medir o vigilar.","Solo calentar el aceite del transformador.","Aumentar la frecuencia de la red.","Eliminar toda protección eléctrica."], answer:0, explain:"Los TT y TC reducen magnitudes, aíslan circuitos y alimentan medición o protección de forma segura."},
      {type:"single", topic:"Error de tensión", q:"¿Qué es error de tensión?", options:["Error que introduce el transformador porque la relación real no es igual a la relación nominal.","La distancia entre dos postes.","La corriente de choque de una barra.","La pérdida de pintura en un aislador."], answer:0, explain:"En transformadores de tensión, el error expresa la diferencia entre transformación real y nominal."},
      {type:"single", topic:"TC protección", q:"¿Cuáles son las clases de precisión para los transformadores de intensidad para protección?", options:["5P y 10P","0,1 y 0,2 únicamente","A y B","Clase verde y clase roja"], answer:0, explain:"Para protección, el material indica clases 5P y 10P."},
      {type:"single", topic:"5P10", q:"¿Qué significa 5P10 en un transformador de corriente para protección?", options:["A 10 veces la corriente nominal primaria, el error compuesto máximo es 5 %.","A 5 voltios y 10 amperios trabaja siempre.","Tiene 5 fases y 10 polos.","Es un cable de 5 mm y 10 kV."], answer:0, explain:"5P10 significa clase de protección con error compuesto máximo de 5 % al factor límite de precisión 10."},
      {type:"single", topic:"TT y TC", q:"¿Qué tipos de transformadores de medida existen?", options:["Transformadores de tensión TT y transformadores de corriente TC.","Solo pararrayos y fusibles.","Únicamente barras de cobre.","Solo seccionadores de puesta a tierra."], answer:0, explain:"Los transformadores de medida principales son TT para tensión y TC para corriente."},
      {type:"match", topic:"Componentes", q:"Relaciona el componente con su función principal.", pairs:[
        ["Interruptor de potencia","Abre y cierra circuitos bajo carga y puede interrumpir fallas"],
        ["Seccionador","Aísla partes del sistema para maniobra o mantenimiento"],
        ["Fusible MT","Protege frente a sobrecorrientes y cortocircuitos"],
        ["Barras de MT","Conducen corriente y conectan equipos de la subestación"]
      ], explain:"Cada componente se selecciona por tensión, corriente, aislamiento y capacidad ante cortocircuito."},
      {type:"single", topic:"Barras", q:"¿Qué se debe verificar en la selección de barras de MT?", options:["Corriente nominal, esfuerzos electrodinámicos, efectos térmicos, resonancia y elevación de temperatura.","Solo el brillo del cobre.","Solo la longitud visual.","Nada, todas las barras sirven igual."], answer:0, explain:"Las barras deben resistir condiciones normales y de falla, tanto eléctrica como mecánicamente."}
    ]
  }
];

let flat = [];
const examEl = document.getElementById('exam');

function normalize(str){
  return (str||'').toString().toLowerCase()
    .normalize('NFD').replace(/[\u0300-\u036f]/g,'')
    .replace(/\s+/g,' ').trim();
}

function renderExam(){
  examEl.innerHTML = '';
  flat = [];
  let globalIndex = 0;
  sections.forEach((section, sIdx)=>{
    const st = document.createElement('div');
    st.className = 'section-title';
    st.innerHTML = `<span>${section.icon}</span><h2>${section.title}</h2>`;
    examEl.appendChild(st);
    section.questions.forEach((q, qIdx)=>{
      globalIndex++;
      const id = `q${globalIndex}`;
      flat.push({...q, id, section:sIdx});
      const div = document.createElement('article');
      div.className = 'question';
      div.id = id;
      div.innerHTML = questionHTML(q, id, globalIndex);
      examEl.appendChild(div);
    });
  });
  document.getElementById('scoreTotal').textContent = flat.length;
  updateProgress();
}

function questionHTML(q,id,num){
  let body = '';
  if(q.type==='single'){
    body = `<div class="options">${q.options.map((o,i)=>`<label class="option"><input type="radio" name="${id}" value="${i}" onchange="updateProgress()"><span>${o}</span></label>`).join('')}</div>`;
  }
  if(q.type==='multi'){
    body = `<div class="options">${q.options.map((o,i)=>`<label class="option"><input type="checkbox" name="${id}" value="${i}" onchange="updateProgress()"><span>${o}</span></label>`).join('')}</div>`;
  }
  if(q.type==='text'){
    body = `<input type="text" name="${id}" placeholder="Escribe la respuesta aquí..." oninput="updateProgress()">`;
  }
  if(q.type==='match'){
    const shuffled = q.pairs.map(p=>p[1]).sort(()=>Math.random()-.5);
    body = `<div class="match-grid">${q.pairs.map((p,i)=>`<div class="match-row"><b>${p[0]}</b><select name="${id}_${i}" onchange="updateProgress()"><option value="">Selecciona...</option>${shuffled.map(opt=>`<option value="${opt}">${opt}</option>`).join('')}</select></div>`).join('')}</div>`;
  }
  return `
    <div class="q-head">
      <div class="q-num">${num}</div>
      <div>
        <div class="q-meta"><span class="tag">${q.topic}</span>${typeLabel(q.type)}</div>
        <div class="q-text">${q.q}</div>
      </div>
    </div>
    ${body}
    <div class="feedback" id="fb_${id}"></div>
  `;
}

function typeLabel(type){
  return type==='single'?'Marcar una':type==='multi'?'Marcar varias':type==='text'?'Completar':'Relacionar';
}

function getAnswer(q){
  if(q.type==='single'){
    const el = document.querySelector(`input[name="${q.id}"]:checked`);
    return el ? Number(el.value) : null;
  }
  if(q.type==='multi'){
    return [...document.querySelectorAll(`input[name="${q.id}"]:checked`)].map(e=>Number(e.value)).sort((a,b)=>a-b);
  }
  if(q.type==='text'){
    const el = document.querySelector(`input[name="${q.id}"]`);
    return normalize(el?.value || '');
  }
  if(q.type==='match'){
    return q.pairs.map((_,i)=>document.querySelector(`select[name="${q.id}_${i}"]`)?.value || '');
  }
}

function isCorrect(q, ans){
  if(q.type==='single') return ans === q.answer;
  if(q.type==='multi') return JSON.stringify(ans) === JSON.stringify([...q.answer].sort((a,b)=>a-b));
  if(q.type==='text') return q.answer.some(a=> ans.includes(normalize(a)) || normalize(a).includes(ans) && ans.length>3);
  if(q.type==='match') return ans.every((v,i)=>v === q.pairs[i][1]);
}

function correctText(q){
  if(q.type==='single') return q.options[q.answer];
  if(q.type==='multi') return q.answer.map(i=>q.options[i]).join('; ');
  if(q.type==='text') return q.answer[0];
  if(q.type==='match') return q.pairs.map(p=>`${p[0]} → ${p[1]}`).join('<br>');
}

function gradeExam(){
  let correct=0;
  flat.forEach(q=>{
    const ans = getAnswer(q);
    const ok = isCorrect(q, ans);
    if(ok) correct++;
    const fb = document.getElementById(`fb_${q.id}`);
    fb.className = `feedback ${ok?'ok':'bad'}`;
    fb.innerHTML = `${ok?'✅ Correcto':'❌ Revisa esta respuesta'}<div class="explain"><b>Respuesta clave:</b> ${correctText(q)}<br><b>Explicación:</b> ${q.explain}</div>`;
  });
  const total=flat.length;
  const wrong=total-correct;
  const pct=Math.round((correct/total)*100);
  document.getElementById('scoreNow').textContent=correct;
  document.getElementById('scoreText').textContent=`${pct}% de logro`;
  document.getElementById('correctCount').textContent=correct;
  document.getElementById('wrongCount').textContent=wrong;
  document.getElementById('percentScore').textContent=pct+'%';
  const level = pct>=90?'Experto':pct>=75?'Bueno':pct>=60?'En proceso':'Repasar base';
  document.getElementById('levelText').textContent=level;
  document.getElementById('resultMessage').innerHTML = `Obtuviste <b>${correct}</b> respuestas correctas de <b>${total}</b>.`;
  document.getElementById('studyTip').innerHTML = tipByScore(pct);
  document.getElementById('resultsBox').classList.add('show');
  document.getElementById('resultsBox').scrollIntoView({behavior:'smooth'});
  updateProgress();
}

function tipByScore(pct){
  if(pct>=90) return 'Excelente. Ya dominas definiciones, criterios y fórmulas. Para cerrar, practica explicar oralmente: subestación, pararrayos, N2XSY, red radial, TT, TC y 5P10.';
  if(pct>=75) return 'Buen avance. Refuerza las preguntas de selección: pararrayos, cable subterráneo, aparamenta y transformadores de medida. Repite el examen una vez más.';
  if(pct>=60) return 'Estás en proceso. Vuelve a estudiar criterios: confiabilidad, flexibilidad, seguridad, caída de tensión, ampacidad, corriente de choque y clases 5P/10P.';
  return 'Necesitas repasar teoría base. Empieza por definiciones: subestación, pararrayos, nivel de aislamiento, esquema unifilar, red radial, N2XSY, aparamenta, TT y TC.';
}

function showAnswers(){
  flat.forEach(q=>{
    const fb=document.getElementById(`fb_${q.id}`);
    fb.className='feedback neutral';
    fb.innerHTML=`💡 <b>Respuesta clave:</b> ${correctText(q)}<div class="explain">${q.explain}</div>`;
  });
}

function resetExam(){
  document.querySelectorAll('input[type="radio"], input[type="checkbox"]').forEach(e=>e.checked=false);
  document.querySelectorAll('input[type="text"]').forEach(e=>e.value='');
  document.querySelectorAll('select').forEach(e=>e.value='');
  document.querySelectorAll('.feedback').forEach(e=>{e.className='feedback';e.innerHTML='';});
  document.getElementById('scoreNow').textContent='0';
  document.getElementById('scoreText').textContent='Responde y presiona “Calificar”.';
  document.getElementById('resultsBox').classList.remove('show');
  updateProgress();
  window.scrollTo({top:0,behavior:'smooth'});
}

function updateProgress(){
  let answered=0;
  flat.forEach(q=>{
    const ans=getAnswer(q);
    if(q.type==='single' && ans!==null) answered++;
    if(q.type==='multi' && ans.length>0) answered++;
    if(q.type==='text' && ans.length>0) answered++;
    if(q.type==='match' && ans.some(v=>v)) answered++;
  });
  const pct=flat.length?Math.round(answered/flat.length*100):0;
  document.getElementById('progressBar').style.width=pct+'%';
}

function scrollToTop(){window.scrollTo({top:0,behavior:'smooth'});}

renderExam();
</script>
</body>
</html>

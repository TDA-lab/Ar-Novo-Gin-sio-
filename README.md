<!doctype html>
<html lang="pt">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Daikin | Calculadora de Ar Novo (m³/h)</title>
  <style>
    :root{
      --daikin-blue:#0097E0;     /* Daikin Blue */
      --daikin-light:#54C3F1;    /* Daikin Light Blue */
      --ink:#0b1220;
      --bg:#ffffff;
      --card:#ffffff;
      --line:#e6e8ef;
      --muted:#4b5563;
    }

    body{
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      margin: 0;
      background: linear-gradient(180deg, rgba(0,151,224,0.10), rgba(84,195,241,0.06) 35%, #fff 75%);
      color: var(--ink);
      line-height: 1.35;
    }

    .wrap{ max-width: 980px; margin: 0 auto; padding: 18px; }

    .topbar{
      background: var(--bg);
      border: 1px solid var(--line);
      border-radius: 16px;
      padding: 14px 16px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      box-shadow: 0 10px 24px rgba(11,18,32,0.06);
    }

    .brand{
      display: flex;
      align-items: center;
      gap: 12px;
      min-width: 260px;
    }

    .brand img{
      height: 34px;
      width: auto;
      display: block;
    }

    .titleblock h1{
      font-size: 1.1rem;
      margin: 0;
    }

    .titleblock .sub{
      margin-top: 4px;
      color: var(--muted);
      font-size: 0.92rem;
    }

    .pill{
      display: inline-block;
      padding: 6px 10px;
      border-radius: 999px;
      background: rgba(0,151,224,0.10);
      border: 1px solid rgba(0,151,224,0.25);
      color: #055e87;
      font-weight: 700;
      font-size: 0.9rem;
      white-space: nowrap;
    }

    .card{
      background: var(--card);
      border: 1px solid var(--line);
      border-radius: 16px;
      padding: 16px;
      margin: 14px 0;
      box-shadow: 0 10px 24px rgba(11,18,32,0.06);
    }

    .grid{
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }

    label{ display:block; font-weight: 700; margin-bottom: 6px; }
    input, select{
      width: 100%;
      padding: 10px 12px;
      border: 1px solid #cfd6e3;
      border-radius: 12px;
      font-size: 1rem;
      outline: none;
      background: #fff;
    }
    input:focus, select:focus{
      border-color: rgba(0,151,224,0.75);
      box-shadow: 0 0 0 4px rgba(0,151,224,0.12);
    }

    .row{
      display:flex;
      gap: 10px;
      align-items:center;
      flex-wrap: wrap;
      margin-top: 12px;
    }

    button{
      padding: 10px 14px;
      border-radius: 12px;
      border: 0;
      cursor: pointer;
      font-weight: 800;
      font-size: 0.98rem;
    }
    button.primary{
      background: var(--daikin-blue);
      color: #fff;
    }
    button.ghost{
      background: rgba(84,195,241,0.18);
      color: #064a66;
      border: 1px solid rgba(84,195,241,0.35);
    }

    .muted{ color: var(--muted); font-size: 0.95rem; }
    .kpi{
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      margin-top: 10px;
    }
    .kpi .box{
      border: 1px solid var(--line);
      border-radius: 14px;
      padding: 12px;
      background: linear-gradient(180deg, rgba(84,195,241,0.10), rgba(0,151,224,0.04));
    }
    .kpi .value{
      font-size: 1.25rem;
      font-weight: 900;
      margin-top: 6px;
    }

    .warn{
      margin-top: 12px;
      padding: 10px 12px;
      border-radius: 12px;
      border: 1px solid rgba(241,79,39,0.35);
      background: rgba(241,79,39,0.10);
      color: #6b2d1b;
      font-weight: 650;
    }

    .formula{
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
      background: rgba(0,0,0,0.04);
      padding: 8px 10px;
      border-radius: 12px;
      border: 1px solid var(--line);
      overflow-x: auto;
      margin-top: 10px;
    }

    @media (max-width: 780px){
      .grid{ grid-template-columns: 1fr; }
      .kpi{ grid-template-columns: 1fr; }
      .brand{ min-width: 0; }
      .topbar{ flex-direction: column; align-items: flex-start; }
    }
  </style>
</head>

<body>
  <div class="wrap">
    <div class="topbar">
      <div class="brand">
        <img
          src="https://upload.wikimedia.org/wikipedia/commons/0/05/DAIKIN_logo.svg"
          alt="Daikin logo"
          referrerpolicy="no-referrer"
        />
        <div class="titleblock">
          <h1>Calculadora de Ar Novo para Ginásios</h1>
          <div class="sub">Saídas: m³/h, L/s, m³/h por pessoa, ACH (renovações/h)</div>
        </div>
      </div>
      <div class="pill">Conversão: 1 L/s = 3,6 m³/h</div>
    </div>

    <div class="card">
      <div class="muted">
        Fórmula base (componente por pessoa + componente por área):
        <div class="formula">V(m³/h) = (N × qₚ × 3,6) + (A × qₐ × 3,6)</div>
      </div>

      <div class="grid" style="margin-top:12px;">
        <div>
          <label for="spaceType">Tipo de espaço</label>
          <select id="spaceType">
            <option value="weights">Musculação / Cardio</option>
            <option value="group">Aulas de grupo (HIIT/Cycling/Crossfit)</option>
            <option value="yoga">Yoga / Pilates</option>
            <option value="custom">Personalizado</option>
          </select>
          <div class="muted" style="margin-top:8px;" id="presetInfo"></div>
        </div>

        <div>
          <label for="people">Nº de pessoas (N)</label>
          <input id="people" type="number" min="0" step="1" value="25" />
        </div>

        <div>
          <label for="area">Área (A) em m²</label>
          <input id="area" type="number" min="0" step="0.1" value="120" />
        </div>

        <div>
          <label for="height">Pé-direito (H) em m</label>
          <input id="height" type="number" min="0" step="0.1" value="3.0" />
          <div class="muted" style="margin-top:8px;">Usado para calcular volume e ACH.</div>
        </div>

        <div>
          <label for="qp">qₚ (L/s·pessoa)</label>
          <input id="qp" type="number" min="0" step="0.1" value="10" />
        </div>

        <div>
          <label for="qa">qₐ (L/s·m²)</label>
          <input id="qa" type="number" min="0" step="0.01" value="0.30" />
        </div>

        <div>
          <label for="safetyFactor">Margem (%)</label>
          <input id="safetyFactor" type="number" min="0" step="1" value="0" />
          <div class="muted" style="margin-top:8px;">Ex.: 10% para cobrir picos e “vida real”.</div>
        </div>
      </div>

      <div class="row">
        <button class="primary" id="calcBtn">Calcular</button>
        <button class="ghost" id="resetBtn">Reset</button>
      </div>
    </div>

    <div class="card">
      <div class="kpi">
        <div class="box">
          <div class="muted">Caudal total (com margem)</div>
          <div class="value" id="kpi_m3h">— m³/h</div>
        </div>
        <div class="box">
          <div class="muted">Caudal total</div>
          <div class="value" id="kpi_ls">— L/s</div>
        </div>
        <div class="box">
          <div class="muted">Caudal específico</div>
          <div class="value" id="kpi_m3h_pessoa">— m³/h·pessoa</div>
        </div>
        <div class="box">
          <div class="muted">ACH (renovações/h)</div>
          <div class="value" id="kpi_ach">— 1/h</div>
        </div>
      </div>

      <div class="muted" style="margin-top:12px;" id="breakdown">—</div>
      <div id="note"></div>
    </div>

    <div class="card">
      <div class="warn">
        Pequeno “puxão de orelhas”: se o teu ginásio tem aulas intensas e muita gente, o problema quase nunca é “a conta”.
        É a realidade: pico de ocupação, distribuição de ar, extração e controlo por CO₂.
      </div>
    </div>
  </div>

  <script>
    const presets = {
      weights: { qp: 10, qa: 0.30, label: "Musculação/Cardio (típico: qₚ 10–12, qₐ 0,3)" },
      group:   { qp: 15, qa: 0.60, label: "Aulas de grupo (típico: qₚ 15–20, qₐ 0,6)" },
      yoga:    { qp:  7, qa: 0.30, label: "Yoga/Pilates (típico: qₚ 7–10, qₐ 0,3)" },
      custom:  { qp: null, qa: null, label: "Personalizado" }
    };

    const el = (id) => document.getElementById(id);

    function fmt(n, d=0) {
      if (!isFinite(n)) return "—";
      return n.toLocaleString("pt-PT", { maximumFractionDigits: d, minimumFractionDigits: d });
    }

    function applyPreset() {
      const type = el("spaceType").value;
      const p = presets[type];

      if (p.qp != null) el("qp").value = p.qp;
      if (p.qa != null) el("qa").value = p.qa;

      el("presetInfo").textContent = `Preset: ${p.label}`;
    }

    function calc() {
      const N  = Number(el("people").value || 0);
      const A  = Number(el("area").value || 0);
      const H  = Number(el("height").value || 0);
      const qp = Number(el("qp").value || 0);
      const qa = Number(el("qa").value || 0);
      const marginPct = Number(el("safetyFactor").value || 0);

      // Base em L/s
      const Vp_ls = N * qp;
      const Va_ls = A * qa;
      const V_ls_base = Vp_ls + Va_ls;

      // Base em m3/h
      const Vp_m3h = Vp_ls * 3.6;
      const Va_m3h = Va_ls * 3.6;
      const V_m3h_base = Vp_m3h + Va_m3h;

      // Margem
      const factor = 1 + (marginPct / 100);
      const V_m3h_final = V_m3h_base * factor;
      const V_ls_final  = V_ls_base  * factor;

      // m3/h por pessoa (com margem) - evita dividir por zero
      const spec_m3h_person = (N > 0) ? (V_m3h_final / N) : NaN;

      // ACH (com margem): ACH = V(m3/h) / Volume(m3)
      const volume = A * H;
      const ach = (volume > 0) ? (V_m3h_final / volume) : NaN;

      // KPIs
      el("kpi_m3h").textContent = `${fmt(V_m3h_final, 0)} m³/h`;
      el("kpi_ls").textContent  = `${fmt(V_ls_final, 1)} L/s`;
      el("kpi_m3h_pessoa").textContent = (N > 0) ? `${fmt(spec_m3h_person, 1)} m³/h·pessoa` : "— m³/h·pessoa";
      el("kpi_ach").textContent = (isFinite(ach)) ? `${fmt(ach, 2)} 1/h` : "— 1/h";

      // Breakdown
      el("breakdown").innerHTML =
        `Pessoas: <b>${fmt(Vp_ls,1)} L/s</b> (${fmt(Vp_m3h,0)} m³/h) &nbsp; | &nbsp; ` +
        `Área: <b>${fmt(Va_ls,1)} L/s</b> (${fmt(Va_m3h,0)} m³/h) &nbsp; | &nbsp; ` +
        `Base: <b>${fmt(V_ls_base,1)} L/s</b> (${fmt(V_m3h_base,0)} m³/h)` +
        (marginPct > 0 ? ` &nbsp; | &nbsp; Com margem (${fmt(marginPct,0)}%): <b>${fmt(V_ls_final,1)} L/s</b> (${fmt(V_m3h_final,0)} m³/h)` : "");

      // Notas “inteligentes” (sem complicar)
      const note = el("note");
      note.innerHTML = "";

      if (N > 0 && A > 0) {
        const dens = N / A; // pessoas/m²
        if (dens > 0.35) {
          note.innerHTML =
            `<div class="warn">Densidade alta (${fmt(dens,2)} pessoas/m²). Se isto for aula intensa, eu desconfiava do qₚ: pensa em 18–20 L/s·pessoa e garante extração/insuflação bem distribuídas.</div>`;
        } else if (dens < 0.08) {
          note.innerHTML =
            `<div class="warn">Densidade baixa (${fmt(dens,2)} pessoas/m²). Se há picos reais (fim do dia, aulas), dimensiona para o pico e usa controlo (CO₂/horário) para não “atirar ar” à toa quando está vazio.</div>`;
        }
      }

      // ACH “sanity check”
      if (isFinite(ach)) {
        if (ach < 2) {
          note.innerHTML += `<div class="warn">ACH baixo (${fmt(ach,2)} 1/h). Pode até “passar” no papel, mas em ginásio é típico dar cheiro e ar pesado nos picos.</div>`;
        } else if (ach > 10) {
          note.innerHTML += `<div class="warn">ACH muito alto (${fmt(ach,2)} 1/h). Confirma se isto faz sentido energeticamente e se não estás a “compensar” má distribuição de ar com caudal bruto.</div>`;
        }
      }
    }

    function resetAll() {
      el("spaceType").value = "weights";
      el("people").value = 25;
      el("area").value = 120;
      el("height").value = 3.0;
      el("safetyFactor").value = 0;
      applyPreset();
      calc();
    }

    el("spaceType").addEventListener("change", () => { applyPreset(); calc(); });
    el("calcBtn").addEventListener("click", calc);
    el("resetBtn").addEventListener("click", resetAll);

    ["people","area","height","qp","qa","safetyFactor"].forEach(id => {
      el(id).addEventListener("input", calc);
    });

    applyPreset();
    calc();
  </script>
</body>
</html>

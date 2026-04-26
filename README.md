import { useState } from "react";

const S = ({ c, children }) => <span style={c}>{children}</span>;

const Badge = ({ t, color }) => {
  const styles = {
    ready: { background: "#e6f4ee", color: "#1a7a42" },
    pending: { background: "#fef3e2", color: "#a05e0a" },
    blue: { background: "#e8f0fe", color: "#1a3fa5" },
    good: { background: "#e6f4ee", color: "#1a7a42" },
    bad: { background: "#fdecea", color: "#a32d2d" },
  };
  return <span style={{ ...styles[color], fontSize: 11, padding: "2px 9px", borderRadius: 20, fontWeight: 500, display: "inline-block" }}>{t}</span>;
};

const Card = ({ children, color }) => (
  <div style={{ background: color || "#f8f8fa", border: "1px solid #e8e8ec", borderRadius: 10, padding: "14px 16px", marginBottom: 12, fontSize: 13, lineHeight: 1.7 }}>{children}</div>
);

const Note = ({ children, type = "info" }) => {
  const styles = { info: { bg: "#eef2fb", border: "#c5d5f055", text: "#1a2a5a" }, warn: { bg: "#fff8ee", border: "#f9a82555", text: "#7a4e0a" }, success: { bg: "#e6f4ee", border: "#1a7a4255", text: "#1a4a2a" }, action: { bg: "#fef4f4", border: "#e8b4b455", text: "#7a1a1a" } };
  const s = styles[type];
  return <div style={{ background: s.bg, border: `1px solid ${s.border}`, borderRadius: 8, padding: "10px 14px", margin: "10px 0", fontSize: 12, color: s.text, lineHeight: 1.7 }}>{children}</div>;
};

const SecTitle = ({ children }) => (
  <div style={{ fontSize: 11, fontWeight: 600, color: "#888", textTransform: "uppercase", letterSpacing: .6, margin: "24px 0 10px" }}>{children}</div>
);

const Tag = ({ children }) => (
  <span style={{ background: "#fff", border: "1px solid #dde", borderRadius: 20, padding: "3px 10px", fontSize: 12, color: "#555", display: "inline-block", margin: "3px" }}>{children}</span>
);

const Member = ({ i, name, role, dark }) => (
  <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 9 }}>
    <div style={{ width: 28, height: 28, borderRadius: "50%", background: dark ? "#222" : "#dce8fa", color: dark ? "#fff" : "#1a3fa5", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 10, fontWeight: 600, flexShrink: 0 }}>{i}</div>
    <div><div style={{ fontSize: 13, fontWeight: 500 }}>{name}</div><div style={{ fontSize: 11, color: "#888" }}>{role}</div></div>
  </div>
);

function Stage({ num, title, status, statusText, children }) {
  const [open, setOpen] = useState(false);
  const c = { done: { bg: "#e6f4ee", t: "#1a7a42", nb: "#1a7a42" }, progress: { bg: "#e8f0fe", t: "#1a3fa5", nb: "#1a5fa5" }, pending: { bg: "#f0f0f4", t: "#888", nb: "#ccc" } }[status];
  return (
    <div style={{ border: "1px solid #e8e8ec", borderRadius: 10, marginBottom: 8, overflow: "hidden" }}>
      <div onClick={() => setOpen(!open)} style={{ display: "flex", alignItems: "center", gap: 10, padding: "13px 16px", cursor: "pointer", background: open ? "#f8f8fa" : "#fff" }}>
        <div style={{ width: 26, height: 26, borderRadius: "50%", background: status === "pending" ? "#f0f0f4" : c.nb, border: status === "pending" ? "1px solid #ddd" : "none", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 11, fontWeight: 600, color: status === "pending" ? "#888" : "#fff", flexShrink: 0 }}>{num}</div>
        <div style={{ flex: 1, fontSize: 13, fontWeight: 500 }}>{title}</div>
        <span style={{ fontSize: 11, padding: "2px 9px", borderRadius: 20, background: c.bg, color: c.t, whiteSpace: "nowrap" }}>{statusText}</span>
        <span style={{ fontSize: 13, color: "#aaa", transform: open ? "rotate(90deg)" : "none", transition: "transform .2s", display: "inline-block" }}>›</span>
      </div>
      {open && <div style={{ padding: "16px 18px 18px", borderTop: "1px solid #f0f0f4", background: "#fafafa", fontSize: 13, lineHeight: 1.75, color: "#2a2a2a" }}>{children}</div>}
    </div>
  );
}

const PhaseHeader = ({ label, name, date, color, bg }) => (
  <div style={{ display: "flex", alignItems: "center", justifyContent: "space-between", padding: "11px 16px", borderRadius: 10, marginBottom: 12, background: bg, borderLeft: `3px solid ${color}` }}>
    <div>
      <div style={{ fontSize: 10, fontWeight: 600, textTransform: "uppercase", letterSpacing: .6, color, marginBottom: 2 }}>{label}</div>
      <div style={{ fontSize: 14, fontWeight: 500 }}>{name}</div>
    </div>
    <div style={{ fontSize: 12, color: "#888" }}>{date}</div>
  </div>
);

export default function App() {
  return (
    <div style={{ background: "#f4f4f6", minHeight: "100vh", padding: "24px 12px", fontFamily: "'Segoe UI',Arial,sans-serif" }}>
      <div style={{ maxWidth: 880, margin: "0 auto", background: "#fff", borderRadius: 16, overflow: "hidden", boxShadow: "0 4px 32px rgba(0,0,0,.10)" }}>

        {/* HEADER */}
        <div style={{ background: "#0d0d0d", padding: "28px 36px", display: "flex", alignItems: "center", justifyContent: "space-between" }}>
          <div>
            <div style={{ color: "#fff", fontSize: 24, fontWeight: 500, letterSpacing: -1 }}>G7Cripto</div>
            <div style={{ color: "#888", fontSize: 12, marginTop: 4 }}>G7 Business Solutions Corp.</div>
          </div>
          <div style={{ textAlign: "center" }}>
            <div style={{ color: "#fff", fontSize: 13, fontWeight: 500, opacity: .85 }}>Alianza Estratégica</div>
            <div style={{ color: "#666", fontSize: 11, marginTop: 4 }}>Hoja de ruta actualizada · 25 de abril de 2026</div>
          </div>
          <div style={{ color: "#fff", fontSize: 22, fontWeight: 500 }}>sinparty<span style={{ fontSize: 12 }}>✦</span></div>
        </div>

        <div style={{ padding: "0 32px 48px" }}>

          {/* LIVE NOTE */}
          <div style={{ background: "#fff8e1", border: "1px solid #f9a825", borderLeft: "4px solid #f9a825", borderRadius: 8, padding: "13px 18px", margin: "24px 0 8px", fontSize: 13, color: "#5a3e00", lineHeight: 1.75, display: "flex", alignItems: "flex-start", gap: 10 }}>
            <span style={{ fontSize: 18, flexShrink: 0 }}>⚡</span>
            <div><strong>Documento en construcción — actualización continua:</strong> Esta Hoja de Ruta es un documento vivo, modificable en tiempo real. La idea es ir perfeccionando cada fase hasta tenerla al 100% antes de su ejecución. <strong>Última actualización: 25 de abril de 2026.</strong></div>
          </div>

          {/* STATUS */}
          <div style={{ background: "#f8f8fa", border: "1px solid #e8e8ec", borderRadius: 10, padding: "16px 20px", margin: "16px 0 24px", display: "grid", gridTemplateColumns: "1fr 1fr", gap: 14 }}>
            {[
              { label: "Infraestructura G7BS", val: "CaaS (Binance) + BaaS (Globa66)", badge: "ready", bt: "✓ Lista" },
              { label: "Integración técnica SinParty", val: "USDC · BTC · ETH", badge: "pending", bt: "En progreso" },
              { label: "Criptos activas", val: "USDC · BTC · ETH (no USDT — política de seguridad)" },
              { label: "Campaña de activación", val: "27, 28 y 29 de abril · Email + WhatsApp · ~27.000 usuarios", badge: "pending", bt: "Activa" },
            ].map((s, i) => (
              <div key={i}>
                <div style={{ color: "#888", fontSize: 11, textTransform: "uppercase", letterSpacing: .5, marginBottom: 4 }}>{s.label}</div>
                <div style={{ fontWeight: 500, fontSize: 13 }}>
                  {s.badge && <span style={{ background: s.badge === "ready" ? "#e6f4ee" : "#fef3e2", color: s.badge === "ready" ? "#1a7a42" : "#a05e0a", fontSize: 11, padding: "2px 8px", borderRadius: 20, fontWeight: 500, marginRight: 6 }}>{s.bt}</span>}
                  {s.val}
                </div>
              </div>
            ))}
          </div>

          {/* CONTEXT */}
          <SecTitle>Contexto estratégico</SecTitle>
          <Card>
            G7 evoluciona de monetizador tradicional a <strong>facilitador de pagos en cripto en LATAM</strong>, operando bajo licencias reguladas:
            <ul style={{ paddingLeft: 18, margin: "8px 0" }}>
              <li><strong>CaaS</strong> — Binance (infraestructura cripto)</li>
              <li><strong>BaaS</strong> — Global66, SEDPE licenciada (pagos fiat en LATAM)</li>
            </ul>
            Modelo diseñado para evitar operar como MSB, enfocado en captación LATAM bajo cumplimiento legal total.
            <Note type="info">G7 no custodia fondos. Opera bajo Binance (cripto) y Global66 (fiat) — ambos aprobados por sus áreas de compliance para el gremio de streaming adulto.</Note>
          </Card>

          {/* PROPUESTA DE PAGOS */}
          <SecTitle>Propuesta de pagos G7BS — App G7Cripto</SecTitle>
          <Card>
            <strong>G7BS</strong>, bajo la app <strong>G7Cripto</strong>, ofrece pagos <strong>100% en cripto</strong> para modelos y estudios en LATAM, con las siguientes condiciones:
            <ul style={{ paddingLeft: 18, margin: "8px 0" }}>
              <li><strong>0.8%</strong> sobre tasa spot en tiempo real — mismo porcentaje para cripto y USD</li>
              <li><strong>Sin fee fijo</strong> — sin cobros adicionales por transacción</li>
              <li><strong>Pagos el mismo día</strong> — disponibilidad inmediata</li>
              <li><strong>0% fee</strong> por envío de cripto desde SinParty (confirmado por SinParty)</li>
            </ul>
            <Note type="info">G7BS no custodia fondos. Opera bajo Binance (CaaS) y Global66 (BaaS) — ambos aprobados por sus áreas de compliance para el gremio de streaming adulto en LATAM.</Note>

          </Card>

          {/* TEAMS */}
          <SecTitle>Equipos de la alianza</SecTitle>
          <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 12, marginBottom: 8 }}>
            <div style={{ background: "#f8f8fa", border: "1px solid #e8e8ec", borderRadius: 10, padding: "16px 18px" }}>
              <div style={{ fontSize: 11, textTransform: "uppercase", letterSpacing: .5, fontWeight: 600, color: "#1a3fa5", marginBottom: 12 }}>G7BS / G7Cripto</div>
              {[["GV","Guillermo L. Valencia","Dirección estratégica"],["HT","Hammer Tapias","Líder principal de la alianza"],["OG","Oscar Gallego (DRILLER)","Director podcast CLICK_FINANCIERO"],["NK","Nicki","Líder de marketing"],["TH","THIAGO","Embajador e influencer de marca"],["KB","Kevin Barragán","Diseñador gráfico"],["OP","Orlando Pacheco","Líder IA / Automatización"],["MR","Equipo Mike Rojo","Dirección y producción audiovisual"]].map(([i,n,r]) => <Member key={i} i={i} name={n} role={r} />)}
            </div>
            <div style={{ background: "#f8f8fa", border: "1px solid #e8e8ec", borderRadius: 10, padding: "16px 18px" }}>
              <div style={{ fontSize: 11, textTransform: "uppercase", letterSpacing: .5, fontWeight: 600, color: "#555", marginBottom: 12 }}>SinParty</div>
              {[["AS","Ashley James","CEO – Jefe de SinParty"],["BG","Bogdan Arsenie","Equipo Europa"],["BR","Brett Solomon","Marketing SinParty"],["DN","Daniela Guzmán","Representante SinParty Latinoamérica"],["CO","Corne","Equipo SinParty"],["LK","Luke","Equipo SinParty"]].map(([i,n,r]) => <Member key={i} i={i} name={n} role={r} dark />)}
              <div style={{ fontSize: 11, textTransform: "uppercase", letterSpacing: .5, fontWeight: 600, color: "#555", margin: "14px 0 8px" }}>Hub de Beneficios</div>
              {["G7Cripto","SinParty","Mandala","Guía Cereza","Michell Arguello","Neum"].map(h => <div key={h} style={{ fontSize: 13, color: "#444", marginBottom: 4 }}>· {h}</div>)}
            </div>
          </div>

          {/* CRONOLOGÍA */}
          <SecTitle>Trazabilidad y cronología</SecTitle>
          <div style={{ borderLeft: "2px solid #1a5fa5", paddingLeft: 16, margin: "8px 0 24px" }}>
            {[["03–10 abril","Contacto inicial","done"],["10–18 abril","Alineación estratégica","done"],["19 abril","Hoja de ruta inicial publicada","done"],["20–24 abril","Validación técnica y comercial","done"],["25 abril","Activación campaña de marketing","progress"],["27–29 abril","Ejecución + LALExpo","pending"],["Mayo","Escalamiento LATAM","pending"]].map(([d,t,s]) => (
              <div key={d} style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 10 }}>
                <div style={{ width: 10, height: 10, borderRadius: "50%", background: s === "done" ? "#1a7a42" : s === "progress" ? "#1a5fa5" : "#ddd", flexShrink: 0, marginLeft: -21 }} />
                <div style={{ fontSize: 12 }}><strong style={{ color: "#1a3fa5" }}>{d}</strong> — {t}</div>
              </div>
            ))}
          </div>

          {/* PHASE I */}
          <PhaseHeader label="Fase I" name="Fundamentos y preparación" date="Completada" color="#1a5fa5" bg="#eef2fb" />

          <Stage num={1} title="Alineación estratégica inicial" status="done" statusText="✓ Completada">
            SinParty aprobó la alianza. Equipo técnico trabajando en integración con USDC, BTC y ETH. G7Cripto operativamente listo: CaaS (Binance) + BaaS (Globa66).
            <Note type="info">Nota estratégica: G7Cripto está completamente listo. Solo se espera la actualización del equipo técnico de SinParty para activar la conexión.</Note>
          </Stage>

          <Stage num={2} title="Propuesta de valor conjunta" status="done" statusText="✓ Aprobada por G7BS">
            <div style={{ fontWeight: 600, marginBottom: 6 }}>Flujo completo G7Cripto</div>
            <ol style={{ paddingLeft: 18, marginBottom: 12 }}>
              {["Descarga de la app","KYC + validación interna","Creación de wallet en Binance","Registro en SinParty","Recepción de pagos en cripto","Disponibilidad inmediata","Conversión vía Global66","Pago en cuenta bancaria local"].map((s,i) => <li key={i} style={{ marginBottom: 4 }}>{s}</li>)}
            </ol>
            <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 12 }}>
              <div>
                <div style={{ fontWeight: 600, fontSize: 12, marginBottom: 6 }}>Beneficios SinParty</div>
                <ul style={{ paddingLeft: 16, fontSize: 13 }}>
                  <li>100% ganancias por 6 meses (referidos)</li>
                  <li>0% fee en cripto (confirmado por Ash)</li>
                  <li>Acceso al programa VIP Creators</li>
                  <li>Pagos diarios confirmados</li>
                </ul>
              </div>
              <div>
                <div style={{ fontWeight: 600, fontSize: 12, marginBottom: 6 }}>Beneficios G7Cripto</div>
                <ul style={{ paddingLeft: 16, fontSize: 13 }}>
                  <li>Pagos mismo día</li>
                  <li>TRM preferencial</li>
                  <li>Solo 0.8% sobre tasa spot</li>
                  <li>Sin fee fijo</li>
                </ul>
              </div>
            </div>
            <Note type="success">✅ Confirmado por SinParty (Ash): Cero fee por pagos en cripto. Retiros instantáneos. Pagos diarios confirmados — pendiente automatización de retiros con G7Cripto como próximo paso técnico.</Note>
            <Note type="info">"Gana más y recibe tu dinero más rápido, sin complicarte."</Note>
          </Stage>

          {/* PHASE II */}
          <PhaseHeader label="Fase II" name="Lalexpo + Campaña de activación" date="27 · 28 · 29 de abril de 2026" color="#d97f0a" bg="#fff8ee" />

          <Stage num={3} title="Campaña de marketing — Email + WhatsApp" status="progress" statusText="Activa">
            <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 12, marginBottom: 12 }}>
              <div>
                <div style={{ fontWeight: 600, fontSize: 12, marginBottom: 6 }}>Detalles</div>
                <ul style={{ paddingLeft: 16, fontSize: 13 }}>
                  <li>Fechas: 27, 28 y 29 de abril</li>
                  <li>Canales: Email + WhatsApp</li>
                  <li>Alcance estimado: ~27.000 usuarios calificados</li>
                </ul>
              </div>
              <div>
                <div style={{ fontWeight: 600, fontSize: 12, marginBottom: 6 }}>Objetivo</div>
                <ul style={{ paddingLeft: 16, fontSize: 13 }}>
                  <li>Captar modelos y estudios</li>
                  <li>Posicionar G7Cripto</li>
                  <li>Generar registros reales</li>
                  <li>Validar el modelo</li>
                </ul>
              </div>
            </div>
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Textos de campaña — Beneficios exclusivos para modelos y studios</div>
            <div style={{ background: "#fff", border: "1px solid #e0e8f5", borderRadius: 8, padding: "12px 14px", marginBottom: 10 }}>
              <ul style={{ paddingLeft: 16, fontSize: 13 }}>
                <li>✅ <strong>100% de tus ganancias por 6 meses</strong> — única plataforma webcam que lo ofrece*</li>
                <li>✅ <strong>Cero comisión en pagos crypto</strong></li>
                <li>✅ <strong>Tasa de cambio preferencial por 6 meses</strong> — cada dólar que ganes en SinParty vale más cuando cobras con G7Cripto</li>
                <li>✅ ¿Prefieres cobrar en USD? <strong>Comisión preferencial de solo 0.8%</strong> — la más baja del mercado</li>
                <li>✅ <strong>Pago el mismo día</strong> que SinParty paga</li>
                <li>✅ <strong>Club VIP de modelos</strong></li>
                <li>✅ <strong>Soporte personalizado en español</strong></li>
              </ul>
              <div style={{ marginTop: 12, paddingTop: 10, borderTop: "1px solid #e8e8ec", fontSize: 12, color: "#444", lineHeight: 1.8 }}>
                📌 Regístrate en SinParty: <span style={{ background: "#eef2fb", padding: "2px 8px", borderRadius: 4, color: "#1a3fa5" }}>[ENLACE_SINPARTY — Orlando completa]</span><br />
                💬 ¿Preguntas? <span style={{ background: "#eef2fb", padding: "2px 8px", borderRadius: 4, color: "#1a3fa5" }}>[ENLACE_WA_G7CRIPTO — Orlando completa]</span><br /><br />
                <span style={{ color: "#888", fontSize: 11 }}>*Aplican T&C del plan de referidos. <a href="https://blog.sinparty.com/blog/news/sinparty-100-percent-project-affiliate-link-6-months/" target="_blank" style={{ color: "#1a5fa5" }}>blog.sinparty.com/100-percent-project</a></span><br />
                <span style={{ color: "#aaa", fontSize: 11 }}>Si no deseas recibir más mensajes, responde STOP o haz clic aquí: {"{{unsubscribe_link}}"}</span>
              </div>
            </div>
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Flujo de ejecución</div>
            <div style={{ display: "flex", gap: 6, flexWrap: "wrap", marginBottom: 10 }}>
              {["Diseño","Automatización","Envío por lotes","Recepción leads","Registro","Activación pagos"].map((f,i) => (
                <div key={i} style={{ display: "flex", alignItems: "center", gap: 4 }}>
                  <span style={{ background: "#1a5fa5", color: "#fff", borderRadius: "50%", width: 20, height: 20, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 10, fontWeight: 600 }}>{i+1}</span>
                  <span style={{ fontSize: 12 }}>{f}</span>
                  {i < 5 && <span style={{ color: "#ccc" }}>→</span>}
                </div>
              ))}
            </div>
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Responsables</div>
            <div style={{ display: "flex", flexWrap: "wrap", gap: 6 }}>
              <Tag>Kevin Barragán — diseño</Tag>
              <Tag>Orlando Pacheco — automatización</Tag>
              <Tag>Hammer Tapias — coordinación</Tag>
            </div>
          </Stage>

          <Stage num={4} title="Lalexpo — Podcast CLICK_FINANCIERO y producción de contenido" status="progress" statusText="En ejecución">
            <div style={{ marginBottom: 10 }}>
              <strong>Agenda:</strong><br />
              · 27 de abril — Bienvenida y preparación<br />
              · 28 y 29 de abril — Evento principal
            </div>
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Podcast CLICK_FINANCIERO</div>
            <ul style={{ paddingLeft: 16, fontSize: 13, marginBottom: 10 }}>
              <li>Entrevistas a CEOs y actores clave de la industria</li>
              <li>Contenido estratégico sobre la alianza G7Cripto x SinParty</li>
              <li>Posicionamiento de la alianza ante el mercado LATAM</li>
              <li><strong>Prioridad: entrevista con Daniela (SinParty)</strong></li>
            </ul>
            <Note type="warn">Estrategia: generar contenido masivo durante el evento para distribuirlo de forma dosificada en las semanas siguientes.</Note>
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Responsables</div>
            <div style={{ display: "flex", flexWrap: "wrap", gap: 6 }}>
              <Tag>Daniela Guzmán (SinParty) — coordinación estratégica evento</Tag>
            <Tag>Oscar Gallego (DRILLER) — dirección del podcast</Tag>
              <Tag>THIAGO — embajador en el evento</Tag>
              <Tag>Nicki — redes en tiempo real y edición</Tag>
              <Tag>Kevin Barragán — piezas gráficas</Tag>
              <Tag>Equipo Mike Rojo — producción audiovisual</Tag>
              <Tag>Hammer Tapias — coordinación + apoyo a DRILLER</Tag>
            </div>
          </Stage>

          {/* PHASE III */}
          <PhaseHeader label="Fase III" name="Escalamiento post-Lalexpo — Tracción y crecimiento LATAM" date="Mayo 2026 en adelante" color="#1a7a42" bg="#eef6f1" />

          <Stage num={5} title="Distribución de contenido y campañas digitales" status="pending" statusText="Pendiente">
            <ul style={{ paddingLeft: 16, fontSize: 13 }}>
              <li>Publicación dosificada de episodios, reels y entrevistas del podcast CLICK_FINANCIERO</li>
              <li>Campañas en redes sociales con THIAGO como voz principal</li>
              <li>Campaña WhatsApp masiva con IA — Orlando Pacheco</li>
              <li>Evaluación de programa de embajadores nacionales e internacionales</li>
            </ul>
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Responsables</div>
            <div style={{ display: "flex", flexWrap: "wrap", gap: 6 }}>
              {["THIAGO","Orlando Pacheco","Kevin Barragán","Nicki","Hammer Tapias"].map(r => <Tag key={r}>{r}</Tag>)}
            </div>
          </Stage>

          <Stage num={6} title="Educación de mercado y posicionamiento" status="pending" statusText="Pendiente">
            <ul style={{ paddingLeft: 16, fontSize: 13 }}>
              <li>Monetización diaria vs. ciclo semanal tradicional</li>
              <li>Comparativa: 0.8% G7Cripto vs. 3.5%–8% Paxum/Littio</li>
              <li>Ventajas del cripto sin fricciones — narrativa modelo caja negra</li>
              <li>Confianza, seguridad y respaldo: Binance CaaS + Globa66 BaaS</li>
            </ul>
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Responsables</div>
            <div style={{ display: "flex", flexWrap: "wrap", gap: 6 }}>
              {["Hammer Tapias","Kevin Barragán","Oscar Gallego (DRILLER) — vía podcast"].map(r => <Tag key={r}>{r}</Tag>)}
            </div>
          </Stage>

          <Stage num={7} title="Conversión y crecimiento conjunto" status="pending" statusText="Pendiente">
            <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 12 }}>
              <div>
                <div style={{ fontWeight: 600, fontSize: 12, marginBottom: 6 }}>Objetivos</div>
                <ul style={{ paddingLeft: 16, fontSize: 13 }}>
                  <li>Atraer modelos y estudios a SinParty desde LATAM</li>
                  <li>Fortalecer confianza comercial en la región</li>
                  <li>Posicionar G7Cripto como pago preferido en SinParty</li>
                  <li>Alianza sostenible con beneficios para ambas partes</li>
                </ul>
              </div>
              <div>
                <div style={{ fontWeight: 600, fontSize: 12, marginBottom: 6 }}>Métricas clave</div>
                <ul style={{ paddingLeft: 16, fontSize: 13 }}>
                  <li>Modelos registrados en SinParty vía G7Cripto</li>
                  <li>Volumen de pagos procesados en cripto</li>
                  <li>Adopción VIP Creators vinculado a G7Cripto</li>
                  <li>Reducción de fricción vs. Paxum / Littio</li>
                  <li>Alcance del contenido generado en Lalexpo</li>
                </ul>
              </div>
            </div>
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Responsables</div>
            <div style={{ display: "flex", flexWrap: "wrap", gap: 6 }}>
              <Tag>Hammer Tapias — seguimiento operativo</Tag>
              <Tag>Daniela Guzmán (SinParty) — coordinación LATAM</Tag>
            </div>
          </Stage>

          <Stage num={8} title="HUB de marcas aliadas — Eventos y workshops por ciudades" status="pending" statusText="Proyecto">
            Proyecto en etapa de conceptualización. La idea es crear un <strong>HUB entre marcas aliadas</strong> que genere beneficios reales y valor tangible para estudios y modelos en LATAM, uniendo fuerzas comerciales, de contenido y de comunidad.
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Marcas participantes propuestas</div>
            <div style={{ display: "flex", flexWrap: "wrap", gap: 6, marginBottom: 10 }}>
              {["G7Cripto","SinParty","Guía Cereza","Mandala","Michelle Arguello","Neum","Estrellas WebCam"].map(m => <Tag key={m}>{m}</Tag>)}
            </div>
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Concepto del evento</div>
            <ul style={{ paddingLeft: 18, fontSize: 13, marginBottom: 10 }}>
              <li>Formato de <strong>workshop o evento por ciudades</strong> — presencial, cercano y replicable</li>
              <li>Formato <strong>nuevo y novedoso</strong> — diferente a los eventos tradicionales de la industria</li>
              <li>Modelo <strong>financieramente viable</strong>: costos compartidos entre todas las marcas, reduciendo la inversión individual</li>
              <li>Cada marca aporta valor desde su especialidad: pagos, plataforma, contenido, comunidad, formación y visibilidad</li>
              <li>Objetivo: posicionar a las marcas aliadas como el ecosistema más completo y confiable para estudios y modelos en LATAM</li>
            </ul>
            <Note type="info">💡 Este HUB no es solo un evento — es la construcción de un ecosistema de valor compartido donde cada marca gana visibilidad, credibilidad y acceso a nuevas audiencias, reduciendo costos al distribuirlos entre todos los participantes.</Note>
            <div style={{ fontWeight: 600, fontSize: 12, margin: "10px 0 6px" }}>Estado</div>
            <Tag>🔵 En conceptualización — pendiente de alinear con marcas participantes</Tag>
          </Stage>

          {/* CONCLUSION */}
          <SecTitle>Estado actual — Alianza en ejecución real</SecTitle>
          <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr 1fr", gap: 10 }}>
            {[["✓","Infraestructura lista","#e6f4ee","#1a7a42"],["✓","Campaña activa","#e8f0fe","#1a3fa5"],["↗","Contenido en producción","#fff8ee","#a05e0a"]].map(([icon,text,bg,color]) => (
              <div key={text} style={{ background: bg, borderRadius: 10, padding: "14px 16px", textAlign: "center" }}>
                <div style={{ fontSize: 24, color, fontWeight: 700, marginBottom: 4 }}>{icon}</div>
                <div style={{ fontSize: 13, fontWeight: 500, color }}>{text}</div>
              </div>
            ))}
          </div>
          <Note type="success" >🚀 Alianza en ejecución real en LATAM — 25 de abril de 2026</Note>

        </div>
        <div style={{ textAlign: "center", padding: 20, fontSize: 11, color: "#aaa", borderTop: "1px solid #f0f0f4" }}>
          Documento preparado por G7 Business Solutions Corp. / G7Cripto · Actualizado: 25 de abril de 2026 · Confidencial
        </div>
      </div>
    </div>
  );
}

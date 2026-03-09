import { useState, useMemo, useEffect, createContext, useContext } from "react";

/* ══════════════════════════════════════════
   認証コンテキスト
══════════════════════════════════════════ */
const AuthContext = createContext(null);
const useAuth = () => useContext(AuthContext);

/* ══════════════════════════════════════════
   デモ用ユーザーDB（本番はSupabase等に置換）
══════════════════════════════════════════ */
const DEMO_USERS = [
  { id: 1, email: "tanaka@demo.com",   password: "demo1234", role: "employee", name: "田中 颯太",   dept: "営業部", joinDate: "2021-04-01", total: 15, used: 5,  halfUsed: 1, avatar: "田", color: "#F9A8D4" },
  { id: 2, email: "suzuki@demo.com",   password: "demo1234", role: "employee", name: "鈴木 美咲",   dept: "経理部", joinDate: "2019-10-01", total: 20, used: 12, halfUsed: 0, avatar: "鈴", color: "#C4B5FD" },
  { id: 3, email: "sato@demo.com",     password: "demo1234", role: "employee", name: "佐藤 健一",   dept: "開発部", joinDate: "2022-04-01", total: 12, used: 3,  halfUsed: 2, avatar: "佐", color: "#93C5FD" },
  { id: 4, email: "yamada@demo.com",   password: "demo1234", role: "employee", name: "山田 花子",   dept: "人事部", joinDate: "2020-07-01", total: 18, used: 8,  halfUsed: 1, avatar: "山", color: "#6EE7B7" },
  { id: 5, email: "ito@demo.com",      password: "demo1234", role: "employee", name: "伊藤 大輔",   dept: "営業部", joinDate: "2023-04-01", total: 10, used: 2,  halfUsed: 0, avatar: "伊", color: "#FCD34D" },
  { id: 6, email: "watanabe@demo.com", password: "demo1234", role: "employee", name: "渡辺 さくら", dept: "開発部", joinDate: "2018-04-01", total: 20, used: 18, halfUsed: 1, avatar: "渡", color: "#FDA4AF" },
  { id: 99, email: "admin@demo.com",   password: "admin1234", role: "admin",   name: "管理者",      dept: "経理部", joinDate: "2015-04-01", total: 20, used: 10, halfUsed: 0, avatar: "管", color: "#F9A8D4" },
];

const INIT_REQUESTS = [
  { id: 1, empId: 1, empName: "田中 颯太",   dept: "営業部", from: "2025-03-15", to: "2025-03-15", type: "full", days: 1,   reason: "私用",    status: "pending",  readByEmp: false },
  { id: 2, empId: 3, empName: "佐藤 健一",   dept: "開発部", from: "2025-03-20", to: "2025-03-21", type: "full", days: 2,   reason: "旅行",    status: "pending",  readByEmp: false },
  { id: 3, empId: 5, empName: "伊藤 大輔",   dept: "営業部", from: "2025-03-18", to: "2025-03-18", type: "am",   days: 0.5, reason: "通院",    status: "approved", readByEmp: false },
  { id: 4, empId: 6, empName: "渡辺 さくら", dept: "開発部", from: "2025-03-25", to: "2025-03-26", type: "full", days: 2,   reason: "帰省",    status: "rejected", readByEmp: false },
  { id: 5, empId: 2, empName: "鈴木 美咲",   dept: "経理部", from: "2025-03-28", to: "2025-03-28", type: "pm",   days: 0.5, reason: "子の行事", status: "approved", readByEmp: true  },
];

const VACATION_MAP = {
  "2025-03-15": [{ empId: 1, name: "田中 颯太",   color: "#F9A8D4", type: "終日" }],
  "2025-03-18": [{ empId: 5, name: "伊藤 大輔",   color: "#FCD34D", type: "午前" }],
  "2025-03-20": [{ empId: 3, name: "佐藤 健一",   color: "#93C5FD", type: "終日" }],
  "2025-03-21": [{ empId: 3, name: "佐藤 健一",   color: "#93C5FD", type: "終日" }],
  "2025-03-25": [{ empId: 6, name: "渡辺 さくら", color: "#FDA4AF", type: "終日" }],
  "2025-03-26": [{ empId: 6, name: "渡辺 さくら", color: "#FDA4AF", type: "終日" }],
  "2025-03-28": [{ empId: 2, name: "鈴木 美咲",   color: "#C4B5FD", type: "午後" }],
  "2025-03-20": [{ empId: 3, name: "佐藤 健一", color: "#93C5FD", type: "終日" }, { empId: 5, name: "伊藤 大輔", color: "#FCD34D", type: "終日" }, { empId: 1, name: "田中 颯太", color: "#F9A8D4", type: "午前" }],
};

const REASON_TEMPLATES = ["通院・医療", "家族行事", "旅行・休暇", "子の学校行事", "帰省", "冠婚葬祭", "その他"];
const DAYS_JP = ["日", "月", "火", "水", "木", "金", "土"];
const STATUS = {
  pending:  { label: "審査中", color: "#FCD34D", bg: "rgba(252,211,77,0.1)",  border: "rgba(252,211,77,0.25)" },
  approved: { label: "承認済", color: "#6EE7B7", bg: "rgba(110,231,183,0.1)", border: "rgba(110,231,183,0.25)" },
  rejected: { label: "却下",   color: "#FDA4AF", bg: "rgba(253,164,175,0.1)", border: "rgba(253,164,175,0.25)" },
};

/* ══════════════════════════════════════════
   CSS
══════════════════════════════════════════ */
const CSS = `
  @import url('https://fonts.googleapis.com/css2?family=Zen+Kaku+Gothic+New:wght@300;400;500;700&family=DM+Mono:wght@400;500&display=swap');
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  ::-webkit-scrollbar { width: 3px; }
  ::-webkit-scrollbar-thumb { background: rgba(249,168,212,0.2); border-radius: 99px; }
  input[type=date]::-webkit-calendar-picker-indicator { filter: invert(0.7) sepia(1) hue-rotate(280deg); }

  @keyframes fadeUp  { from{opacity:0;transform:translateY(16px)} to{opacity:1;transform:translateY(0)} }
  @keyframes shimmer { from{background-position:-200% center} to{background-position:200% center} }
  @keyframes floatUp { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-6px)} }
  @keyframes pulse2  { 0%,100%{opacity:1} 50%{opacity:0.4} }
  @keyframes bloom   { from{transform:scale(0.94);opacity:0} to{transform:scale(1);opacity:1} }
  @keyframes shake   { 0%,100%{transform:translateX(0)} 25%{transform:translateX(-6px)} 75%{transform:translateX(6px)} }
  @keyframes slideIn { from{opacity:0;transform:translateY(-8px)} to{opacity:1;transform:translateY(0)} }

  .fade-up  { animation: fadeUp 0.45s cubic-bezier(0.22,1,0.36,1) both; }
  .bloom    { animation: bloom  0.3s  cubic-bezier(0.22,1,0.36,1) both; }
  .shake    { animation: shake  0.4s  ease; }

  .glass {
    background: rgba(255,255,255,0.035);
    backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
    border: 1px solid rgba(255,255,255,0.08); border-radius: 20px;
  }
  .glass-hover { transition: background 0.2s, border-color 0.2s, transform 0.2s; }
  .glass-hover:hover { background: rgba(255,255,255,0.055) !important; border-color: rgba(249,168,212,0.2) !important; transform: translateY(-2px); }

  .btn-sakura {
    background: linear-gradient(135deg,#f9a8d4cc,#c084fccc);
    backdrop-filter: blur(10px); border: 1px solid rgba(249,168,212,0.4);
    color:#fff; font-weight:700; font-size:14px; padding:13px 24px;
    border-radius:14px; cursor:pointer; width:100%;
    font-family:'Zen Kaku Gothic New',sans-serif; letter-spacing:0.06em;
    transition:all 0.2s; text-shadow:0 1px 4px rgba(0,0,0,0.3);
  }
  .btn-sakura:hover  { transform:translateY(-2px); box-shadow:0 8px 32px rgba(249,168,212,0.3); }
  .btn-sakura:disabled { opacity:0.35; cursor:not-allowed; transform:none; box-shadow:none; }

  .input-field {
    width:100%; padding:11px 14px;
    background:rgba(255,255,255,0.04); border:1px solid rgba(255,255,255,0.08);
    border-radius:12px; color:#F9FAFB; font-size:14px; outline:none;
    font-family:'Zen Kaku Gothic New',sans-serif; colorScheme:dark; transition:border-color 0.2s,background 0.2s;
  }
  .input-field:focus { border-color:rgba(249,168,212,0.5); background:rgba(249,168,212,0.06); }
  .input-field.error { border-color:rgba(253,164,175,0.6) !important; background:rgba(253,164,175,0.06) !important; }
  .input-field::placeholder { color:rgba(255,255,255,0.2); }

  .nav-btn { transition:all 0.15s; }
  .nav-btn:hover { background:rgba(249,168,212,0.08) !important; }
  .tab-btn { transition:all 0.15s; font-family:'Zen Kaku Gothic New',sans-serif; }
  .tab-btn:hover { color:#F9FAFB !important; }

  .template-chip {
    padding:6px 12px; border-radius:99px; font-size:12px; cursor:pointer;
    font-family:'Zen Kaku Gothic New',sans-serif; transition:all 0.15s;
    background:rgba(255,255,255,0.04); border:1px solid rgba(255,255,255,0.08); color:rgba(255,255,255,0.5);
  }
  .template-chip:hover { background:rgba(249,168,212,0.12); border-color:rgba(249,168,212,0.3); color:#F9A8D4; }
  .template-chip.active { background:rgba(249,168,212,0.15); border-color:rgba(249,168,212,0.4); color:#F9A8D4; }

  .cal-day { transition:all 0.15s; cursor:pointer; }
  .cal-day:hover { background:rgba(249,168,212,0.08) !important; border-color:rgba(249,168,212,0.2) !important; }

  .btn-sm-approve { padding:7px 14px; border-radius:9px; font-size:12px; font-weight:700; cursor:pointer; font-family:'Zen Kaku Gothic New',sans-serif; transition:all 0.15s; background:rgba(110,231,183,0.1); border:1px solid rgba(110,231,183,0.3); color:#6EE7B7; }
  .btn-sm-approve:hover { background:rgba(110,231,183,0.2); }
  .btn-sm-reject  { padding:7px 14px; border-radius:9px; font-size:12px; font-weight:700; cursor:pointer; font-family:'Zen Kaku Gothic New',sans-serif; transition:all 0.15s; background:rgba(253,164,175,0.1); border:1px solid rgba(253,164,175,0.3); color:#FDA4AF; }
  .btn-sm-reject:hover  { background:rgba(253,164,175,0.2); }

  .toast { animation: slideIn 0.3s ease; }

  @media (max-width:768px) {
    .sidebar { display:none !important; }
    .mobile-nav { display:flex !important; }
    .main-pad { padding:20px 16px 96px !important; }
    .stats-grid { grid-template-columns:1fr 1fr !important; }
    .emp-grid   { grid-template-columns:1fr !important; }
    .req-row    { flex-direction:column; align-items:flex-start !important; gap:12px !important; }
    .req-actions { align-self:flex-end; }
    .date-grid  { grid-template-columns:1fr !important; }
  }
  @media (min-width:769px) { .mobile-nav { display:none !important; } }
`;

/* ══════════════════════════════════════════
   汎用コンポーネント
══════════════════════════════════════════ */
function Toast({ toasts }) {
  return (
    <div style={{ position: "fixed", top: 20, right: 20, zIndex: 9999, display: "flex", flexDirection: "column", gap: 10, pointerEvents: "none" }}>
      {toasts.map(t => (
        <div key={t.id} className="toast" style={{
          padding: "12px 18px", borderRadius: 12, fontSize: 13, fontWeight: 600,
          background: t.type === "success" ? "rgba(110,231,183,0.15)" : t.type === "error" ? "rgba(253,164,175,0.15)" : "rgba(249,168,212,0.15)",
          border: `1px solid ${t.type === "success" ? "rgba(110,231,183,0.35)" : t.type === "error" ? "rgba(253,164,175,0.35)" : "rgba(249,168,212,0.35)"}`,
          color: t.type === "success" ? "#6EE7B7" : t.type === "error" ? "#FDA4AF" : "#F9A8D4",
          backdropFilter: "blur(20px)", maxWidth: 280, pointerEvents: "auto",
          display: "flex", alignItems: "center", gap: 8,
        }}>
          <span>{t.type === "success" ? "✓" : t.type === "error" ? "✕" : "🔔"}</span>
          {t.message}
        </div>
      ))}
    </div>
  );
}

function useToast() {
  const [toasts, setToasts] = useState([]);
  const addToast = (message, type = "info") => {
    const id = Date.now();
    setToasts(t => [...t, { id, message, type }]);
    setTimeout(() => setToasts(t => t.filter(x => x.id !== id)), 3500);
  };
  return { toasts, addToast };
}

function Avatar({ emp, size = 36 }) {
  return (
    <div style={{
      width: size, height: size, borderRadius: "50%",
      background: `${emp.color}18`, border: `1.5px solid ${emp.color}44`,
      display: "flex", alignItems: "center", justifyContent: "center",
      fontSize: size * 0.37, fontWeight: 700, color: emp.color, flexShrink: 0,
    }}>{emp.avatar}</div>
  );
}

function StatusBadge({ status }) {
  const s = STATUS[status];
  return (
    <span style={{
      display: "inline-flex", alignItems: "center", gap: 5, fontSize: 11, fontWeight: 700,
      padding: "4px 11px", borderRadius: 99, background: s.bg, color: s.color, border: `1px solid ${s.border}`,
    }}>
      <span style={{ width: 5, height: 5, borderRadius: "50%", background: s.color, flexShrink: 0, animation: status === "pending" ? "pulse2 1.6s infinite" : "none" }} />
      {s.label}
    </span>
  );
}

function GlassCard({ children, style = {}, className = "" }) {
  return (
    <div className={`glass glass-hover ${className}`} style={{ padding: "22px 24px", ...style }}>
      {children}
    </div>
  );
}

function FieldError({ msg }) {
  return msg ? <p style={{ fontSize: 11, color: "#FDA4AF", marginTop: 5 }}>⚠ {msg}</p> : null;
}

/* ══════════════════════════════════════════
   ログイン画面
══════════════════════════════════════════ */
function LoginScreen({ onLogin }) {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [errors, setErrors] = useState({});
  const [loading, setLoading] = useState(false);
  const [shakeKey, setShakeKey] = useState(0);
  const [showPolicy, setShowPolicy] = useState(false);
  const [agreedPolicy, setAgreedPolicy] = useState(false);

  function validate() {
    const e = {};
    if (!email.trim()) e.email = "メールアドレスを入力してください";
    else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) e.email = "メールアドレスの形式が正しくありません";
    if (!password) e.password = "パスワードを入力してください";
    else if (password.length < 6) e.password = "パスワードは6文字以上です";
    return e;
  }

  async function handleLogin() {
    const e = validate();
    if (Object.keys(e).length) { setErrors(e); setShakeKey(k => k + 1); return; }
    setLoading(true);
    await new Promise(r => setTimeout(r, 800)); // 擬似通信
    const user = DEMO_USERS.find(u => u.email === email && u.password === password);
    if (!user) {
      setErrors({ auth: "メールアドレスまたはパスワードが違います" });
      setShakeKey(k => k + 1);
      setLoading(false);
      return;
    }
    onLogin(user);
  }

  return (
    <div style={{
      minHeight: "100vh", display: "flex", flexDirection: "column", alignItems: "center", justifyContent: "center",
      background: "linear-gradient(135deg,#0d0815 0%,#100a1a 40%,#0a0f1a 100%)",
      fontFamily: "'Zen Kaku Gothic New', sans-serif", padding: 20, position: "relative", overflow: "hidden",
    }}>
      <style>{CSS}</style>
      <div style={{ position: "absolute", width: 500, height: 500, borderRadius: "50%", top: -150, right: -150, background: "radial-gradient(circle,rgba(249,168,212,0.07) 0%,transparent 70%)", pointerEvents: "none" }} />
      <div style={{ position: "absolute", width: 400, height: 400, borderRadius: "50%", bottom: -100, left: -100, background: "radial-gradient(circle,rgba(192,132,252,0.05) 0%,transparent 70%)", pointerEvents: "none" }} />

      {/* デモバナー */}
      <div style={{ background: "rgba(249,168,212,0.08)", border: "1px solid rgba(249,168,212,0.2)", borderRadius: 12, padding: "10px 18px", marginBottom: 28, fontSize: 12, color: "#F9A8D4", textAlign: "center", maxWidth: 360 }}>
        🌸 デモ版 — 社員: tanaka@demo.com / demo1234　管理者: admin@demo.com / admin1234
      </div>

      <div key={shakeKey} className={`glass bloom ${shakeKey > 0 && errors.auth ? "shake" : ""}`} style={{ width: "100%", maxWidth: 380, padding: "36px 32px" }}>
        <div style={{ textAlign: "center", marginBottom: 28 }}>
          <p style={{ fontSize: 22, fontWeight: 700, color: "#F9A8D4", letterSpacing: "0.1em", marginBottom: 6 }}>🌸 KYUUKA</p>
          <p style={{ fontSize: 13, color: "rgba(255,255,255,0.35)" }}>有給管理システム</p>
        </div>

        {errors.auth && (
          <div style={{ background: "rgba(253,164,175,0.1)", border: "1px solid rgba(253,164,175,0.3)", borderRadius: 10, padding: "10px 14px", marginBottom: 18, fontSize: 13, color: "#FDA4AF" }}>
            {errors.auth}
          </div>
        )}

        <div style={{ marginBottom: 16 }}>
          <label style={{ fontSize: 11, color: "rgba(255,255,255,0.35)", display: "block", marginBottom: 7, letterSpacing: "0.07em" }}>メールアドレス</label>
          <input className={`input-field ${errors.email ? "error" : ""}`} type="email" value={email}
            onChange={e => { setEmail(e.target.value); setErrors(p => ({ ...p, email: "", auth: "" })); }}
            placeholder="email@example.com"
            onKeyDown={e => e.key === "Enter" && handleLogin()}
          />
          <FieldError msg={errors.email} />
        </div>

        <div style={{ marginBottom: 22 }}>
          <label style={{ fontSize: 11, color: "rgba(255,255,255,0.35)", display: "block", marginBottom: 7, letterSpacing: "0.07em" }}>パスワード</label>
          <input className={`input-field ${errors.password ? "error" : ""}`} type="password" value={password}
            onChange={e => { setPassword(e.target.value); setErrors(p => ({ ...p, password: "", auth: "" })); }}
            placeholder="••••••••"
            onKeyDown={e => e.key === "Enter" && handleLogin()}
          />
          <FieldError msg={errors.password} />
        </div>

        <div style={{ display: "flex", alignItems: "flex-start", gap: 10, marginBottom: 22 }}>
          <input type="checkbox" id="policy" checked={agreedPolicy} onChange={e => setAgreedPolicy(e.target.checked)}
            style={{ marginTop: 2, accentColor: "#F9A8D4", cursor: "pointer", flexShrink: 0 }} />
          <label htmlFor="policy" style={{ fontSize: 12, color: "rgba(255,255,255,0.4)", lineHeight: 1.5, cursor: "pointer" }}>
            <span onClick={() => setShowPolicy(true)} style={{ color: "#F9A8D4", textDecoration: "underline", cursor: "pointer" }}>利用規約・プライバシーポリシー</span>に同意します
          </label>
        </div>

        <button className="btn-sakura" disabled={loading || !agreedPolicy} onClick={handleLogin}>
          {loading ? "ログイン中…" : "ログイン"}
        </button>
      </div>

      {/* プライバシーポリシーモーダル */}
      {showPolicy && <PolicyModal onClose={() => setShowPolicy(false)} />}
    </div>
  );
}

/* ══════════════════════════════════════════
   利用規約・プライバシーポリシーモーダル
══════════════════════════════════════════ */
function PolicyModal({ onClose }) {
  const [tab, setTab] = useState("terms");
  return (
    <div style={{
      position: "fixed", inset: 0, zIndex: 9999,
      background: "rgba(0,0,0,0.7)", backdropFilter: "blur(8px)",
      display: "flex", alignItems: "center", justifyContent: "center", padding: 20,
    }} onClick={onClose}>
      <div className="glass bloom" style={{ width: "100%", maxWidth: 560, maxHeight: "80vh", display: "flex", flexDirection: "column", padding: 0, overflow: "hidden" }}
        onClick={e => e.stopPropagation()}>
        <div style={{ padding: "22px 24px 0", borderBottom: "1px solid rgba(255,255,255,0.07)", flexShrink: 0 }}>
          <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 16 }}>
            <p style={{ fontSize: 15, fontWeight: 700, color: "#F9FAFB" }}>利用規約・プライバシーポリシー</p>
            <button onClick={onClose} style={{ background: "none", border: "none", color: "rgba(255,255,255,0.4)", fontSize: 20, cursor: "pointer" }}>×</button>
          </div>
          <div style={{ display: "flex", gap: 4 }}>
            {[["terms", "利用規約"], ["privacy", "プライバシーポリシー"]].map(([id, label]) => (
              <button key={id} className="tab-btn" onClick={() => setTab(id)} style={{
                padding: "7px 16px", borderRadius: "8px 8px 0 0", border: "none", cursor: "pointer",
                background: tab === id ? "rgba(249,168,212,0.1)" : "transparent",
                color: tab === id ? "#F9A8D4" : "rgba(255,255,255,0.35)",
                fontSize: 12, fontWeight: tab === id ? 700 : 400,
              }}>{label}</button>
            ))}
          </div>
        </div>

        <div style={{ padding: "20px 24px", overflowY: "auto", flex: 1, fontSize: 13, color: "rgba(255,255,255,0.6)", lineHeight: 1.8 }}>
          {tab === "terms" ? (
            <div>
              <Section title="第1条（目的）">本サービス「KYUUKA」（以下「本サービス」）は、企業の有給休暇管理を効率化することを目的としたWebアプリケーションです。</Section>
              <Section title="第2条（利用資格）">本サービスは、管理者によって登録されたユーザーのみが利用できます。登録情報は正確かつ最新の情報を入力してください。</Section>
              <Section title="第3条（禁止事項）">以下の行為を禁止します。①他者のアカウントへの不正アクセス ②虚偽の申請情報の入力 ③サービスの逆コンパイル・改ざん ④本サービスを利用した違法行為</Section>
              <Section title="第4条（免責事項）">本サービスは現状有姿で提供されます。システム障害・データ消失等による損害について、運営者は責任を負いません。本サービスは労働基準法の一般的な解釈に基づいており、法的アドバイスを提供するものではありません。</Section>
              <Section title="第5条（変更・終了）">運営者はサービス内容を予告なく変更・終了する場合があります。重要な変更はメールまたはアプリ内通知でお知らせします。</Section>
              <Section title="第6条（準拠法）">本規約は日本法に準拠し、東京地方裁判所を専属合意管轄裁判所とします。</Section>
            </div>
          ) : (
            <div>
              <Section title="収集する情報">氏名・メールアドレス・所属部署・入社日・有給申請情報など、サービス提供に必要な情報を収集します。</Section>
              <Section title="利用目的">①有給申請・承認機能の提供 ②取得状況の集計・表示 ③法令遵守状況の管理（労働基準法第39条）</Section>
              <Section title="第三者提供">法令に基づく場合を除き、ユーザーの個人情報を第三者に提供しません。</Section>
              <Section title="データの保管">収集したデータは暗号化して保管し、適切なアクセス制御を実施します。退職等によるアカウント削除後、データは90日以内に完全削除されます。</Section>
              <Section title="Cookie">本サービスはセッション管理のためCookieを使用します。ブラウザの設定で無効化できますが、一部機能が利用できなくなる場合があります。</Section>
              <Section title="お問い合わせ">個人情報に関するお問い合わせは admin@kyuuka-app.com までご連絡ください。</Section>
            </div>
          )}
        </div>
      </div>
    </div>
  );
}

function Section({ title, children }) {
  return (
    <div style={{ marginBottom: 18 }}>
      <p style={{ fontSize: 13, fontWeight: 700, color: "#F9A8D4", marginBottom: 6 }}>{title}</p>
      <p style={{ fontSize: 12, color: "rgba(255,255,255,0.5)", lineHeight: 1.8 }}>{children}</p>
    </div>
  );
}

/* ══════════════════════════════════════════
   通知パネル
══════════════════════════════════════════ */
function NotificationPanel({ requests, currentUser, onRead, onClose }) {
  const myNotifs = requests.filter(r => r.empId === currentUser.id && !r.readByEmp && r.status !== "pending");

  return (
    <div style={{
      position: "absolute", top: 50, right: 0, width: 300, zIndex: 999,
      background: "rgba(13,8,21,0.95)", backdropFilter: "blur(20px)",
      border: "1px solid rgba(249,168,212,0.2)", borderRadius: 16,
      boxShadow: "0 20px 60px rgba(0,0,0,0.5)", overflow: "hidden",
    }} className="bloom">
      <div style={{ padding: "14px 18px", borderBottom: "1px solid rgba(255,255,255,0.07)", display: "flex", justifyContent: "space-between", alignItems: "center" }}>
        <p style={{ fontSize: 13, fontWeight: 700, color: "#F9FAFB" }}>通知</p>
        {myNotifs.length > 0 && (
          <button onClick={() => { myNotifs.forEach(n => onRead(n.id)); }} style={{ background: "none", border: "none", fontSize: 11, color: "#F9A8D4", cursor: "pointer" }}>すべて既読</button>
        )}
      </div>
      {myNotifs.length === 0
        ? <p style={{ padding: "20px 18px", fontSize: 13, color: "rgba(255,255,255,0.3)", textAlign: "center" }}>新しい通知はありません</p>
        : myNotifs.map(r => (
          <div key={r.id} onClick={() => onRead(r.id)} style={{
            padding: "13px 18px", borderBottom: "1px solid rgba(255,255,255,0.05)",
            cursor: "pointer", transition: "background 0.15s",
            background: "rgba(255,255,255,0.02)",
          }}>
            <div style={{ display: "flex", alignItems: "center", gap: 8, marginBottom: 4 }}>
              <span style={{ width: 7, height: 7, borderRadius: "50%", background: r.status === "approved" ? "#6EE7B7" : "#FDA4AF", flexShrink: 0 }} />
              <p style={{ fontSize: 13, fontWeight: 600, color: "#F9FAFB" }}>
                申請が{r.status === "approved" ? "承認" : "却下"}されました
              </p>
            </div>
            <p style={{ fontSize: 11, color: "rgba(255,255,255,0.35)", paddingLeft: 15 }}>{r.from}〜{r.to} · {r.reason}</p>
          </div>
        ))
      }
    </div>
  );
}

/* ══════════════════════════════════════════
   有給消滅アラート & 5日義務バー
══════════════════════════════════════════ */
function ExpiryAlert({ emp }) {
  const rem = emp.total - emp.used - emp.halfUsed * 0.5;
  if (rem <= 0 || rem > 5) return null;
  return (
    <div style={{ background: "rgba(252,211,77,0.07)", border: "1px solid rgba(252,211,77,0.25)", borderRadius: 14, padding: "14px 18px", marginBottom: 16, display: "flex", alignItems: "center", gap: 12 }}>
      <span style={{ fontSize: 20, animation: "floatUp 2s ease-in-out infinite", flexShrink: 0 }}>⚠️</span>
      <div>
        <p style={{ fontSize: 13, fontWeight: 700, color: "#FCD34D", marginBottom: 2 }}>有給消滅アラート</p>
        <p style={{ fontSize: 12, color: "rgba(255,255,255,0.45)" }}>
          リセットまで残 <span style={{ color: "#FCD34D", fontWeight: 700 }}>{rem}日</span> が消滅する前に取得しましょう。年度末前に申請することをお勧めします。
        </p>
      </div>
    </div>
  );
}

function ObligationBar({ used }) {
  const pct = Math.min(100, Math.round((used / 5) * 100));
  const done = used >= 5;
  return (
    <GlassCard style={{ marginBottom: 16 }}>
      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 10 }}>
        <div>
          <p style={{ fontSize: 13, fontWeight: 600, color: "#F9FAFB", marginBottom: 2 }}>5日取得義務（労基法第39条）</p>
          <p style={{ fontSize: 11, color: "rgba(255,255,255,0.3)" }}>年5日の取得が法律で義務付けられています</p>
        </div>
        <span style={{ fontSize: 11, fontWeight: 700, padding: "4px 10px", borderRadius: 99, background: done ? "rgba(110,231,183,0.12)" : "rgba(252,211,77,0.1)", color: done ? "#6EE7B7" : "#FCD34D", border: `1px solid ${done ? "rgba(110,231,183,0.3)" : "rgba(252,211,77,0.25)"}` }}>
          {done ? "✓ 達成" : "未達成"}
        </span>
      </div>
      <div style={{ height: 7, background: "rgba(255,255,255,0.07)", borderRadius: 99, overflow: "hidden", marginBottom: 8 }}>
        <div style={{ height: "100%", width: `${pct}%`, background: done ? "linear-gradient(90deg,#6EE7B7,#34D399)" : "linear-gradient(90deg,#F9A8D4,#C084FC)", borderRadius: 99, transition: "width 0.8s cubic-bezier(0.4,0,0.2,1)" }} />
      </div>
      <div style={{ display: "flex", justifyContent: "space-between", fontSize: 11, color: "rgba(255,255,255,0.3)" }}>
        <span>取得済み {used}日</span><span>目標 5日</span>
      </div>
    </GlassCard>
  );
}

/* ══════════════════════════════════════════
   ダッシュボード
══════════════════════════════════════════ */
function Dashboard({ emp, requests }) {
  const totalUsed = emp.used + emp.halfUsed * 0.5;
  const rem = emp.total - totalUsed;
  const pct = Math.round((totalUsed / emp.total) * 100);
  const myReqs = requests.filter(r => r.empId === emp.id);

  return (
    <div className="fade-up">
      <ExpiryAlert emp={emp} />
      <GlassCard style={{ marginBottom: 16, position: "relative", overflow: "hidden", padding: "28px 32px" }}>
        <div style={{ position: "absolute", right: -40, top: -40, width: 200, height: 200, borderRadius: "50%", background: "rgba(249,168,212,0.04)", pointerEvents: "none" }} />
        <p style={{ fontSize: 11, color: "rgba(255,255,255,0.3)", marginBottom: 8, letterSpacing: "0.1em" }}>GOOD MORNING</p>
        <h2 style={{ fontSize: 22, fontWeight: 700, color: "#F9FAFB", marginBottom: 4 }}>{emp.name} さん</h2>
        <p style={{ fontSize: 13, color: "rgba(255,255,255,0.35)" }}>{emp.dept} · 2025年度</p>
      </GlassCard>

      <div className="stats-grid" style={{ display: "grid", gridTemplateColumns: "repeat(3,1fr)", gap: 12, marginBottom: 16 }}>
        {[
          { label: "残日数",       val: rem,       unit: "日", color: "#F9A8D4", sub: `付与 ${emp.total}日` },
          { label: "取得済み",     val: totalUsed, unit: "日", color: "#C4B5FD", sub: `取得率 ${pct}%` },
          { label: "リセットまで", val: 22,        unit: "日", color: "#FCD34D", sub: "2025年4月1日" },
        ].map(s => (
          <GlassCard key={s.label} style={{ padding: "18px 18px" }}>
            <p style={{ fontSize: 10, color: "rgba(255,255,255,0.3)", marginBottom: 10, letterSpacing: "0.07em" }}>{s.label}</p>
            <div style={{ display: "flex", alignItems: "baseline", gap: 3, marginBottom: 5 }}>
              <span style={{ fontSize: 30, fontWeight: 700, color: s.color, fontFamily: "'DM Mono', monospace" }}>{s.val}</span>
              <span style={{ fontSize: 12, color: "rgba(255,255,255,0.3)" }}>{s.unit}</span>
            </div>
            <p style={{ fontSize: 10, color: "rgba(255,255,255,0.2)" }}>{s.sub}</p>
          </GlassCard>
        ))}
      </div>

      <ObligationBar used={emp.used} />

      <GlassCard style={{ marginBottom: 16 }}>
        <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 12 }}>
          <span style={{ fontSize: 13, fontWeight: 600, color: "#F9FAFB" }}>年間取得率</span>
          <span style={{ fontFamily: "'DM Mono'", fontSize: 13, color: "#F9A8D4" }}>{pct}%</span>
        </div>
        <div style={{ height: 6, background: "rgba(255,255,255,0.07)", borderRadius: 99, overflow: "hidden" }}>
          <div style={{ height: "100%", width: `${pct}%`, background: "linear-gradient(90deg,#F9A8D4,#C084FC,#818CF8)", backgroundSize: "200% auto", borderRadius: 99, animation: "shimmer 3s linear infinite" }} />
        </div>
        <div style={{ display: "flex", justifyContent: "space-between", marginTop: 7, fontSize: 11, color: "rgba(255,255,255,0.2)" }}>
          <span>0日</span><span>{emp.total}日</span>
        </div>
      </GlassCard>

      <GlassCard>
        <p style={{ fontSize: 13, fontWeight: 600, color: "#F9FAFB", marginBottom: 16 }}>最近の申請</p>
        {myReqs.length === 0
          ? <p style={{ fontSize: 13, color: "rgba(255,255,255,0.3)", textAlign: "center", padding: "24px 0" }}>申請履歴はありません</p>
          : myReqs.map((r, i) => (
            <div key={r.id} style={{ display: "flex", alignItems: "center", justifyContent: "space-between", padding: "13px 0", borderBottom: i < myReqs.length - 1 ? "1px solid rgba(255,255,255,0.06)" : "none" }}>
              <div>
                <div style={{ display: "flex", alignItems: "center", gap: 7, marginBottom: 3 }}>
                  <p style={{ fontSize: 13, color: "#F9FAFB", fontWeight: 500 }}>{r.from}　〜　{r.to}</p>
                  {r.type !== "full" && <span style={{ fontSize: 10, padding: "2px 7px", borderRadius: 99, background: "rgba(249,168,212,0.12)", color: "#F9A8D4", border: "1px solid rgba(249,168,212,0.2)", fontWeight: 700 }}>{r.type === "am" ? "午前休" : "午後休"}</span>}
                </div>
                <p style={{ fontSize: 11, color: "rgba(255,255,255,0.35)" }}>{r.reason} · {r.days}日</p>
              </div>
              <StatusBadge status={r.status} />
            </div>
          ))
        }
      </GlassCard>
    </div>
  );
}

/* ══════════════════════════════════════════
   申請画面（エラーハンドリング強化）
══════════════════════════════════════════ */
function Apply({ emp, onSubmit }) {
  const [form, setForm] = useState({ from: "", to: "", type: "full", reason: "" });
  const [errors, setErrors] = useState({});
  const [sent, setSent] = useState(false);
  const [loading, setLoading] = useState(false);
  const totalUsed = emp.used + emp.halfUsed * 0.5;
  const rem = emp.total - totalUsed;

  const calcDays = useMemo(() => {
    if (!form.from) return null;
    if (form.type !== "full") return 0.5;
    if (!form.to) return null;
    const d = Math.round((new Date(form.to) - new Date(form.from)) / 86400000) + 1;
    return d > 0 ? d : null;
  }, [form.from, form.to, form.type]);

  function validate() {
    const e = {};
    if (!form.from) { e.from = "日付を選択してください"; }
    else {
      const fromDate = new Date(form.from);
      const today = new Date(); today.setHours(0,0,0,0);
      if (fromDate < today) e.from = "過去の日付は選択できません";
    }
    if (form.type === "full") {
      if (!form.to) e.to = "終了日を選択してください";
      else if (new Date(form.to) < new Date(form.from)) e.to = "終了日は開始日以降にしてください";
    }
    if (!form.reason.trim()) e.reason = "理由を入力または選択してください";
    if (calcDays && calcDays > rem) e.days = `申請日数（${calcDays}日）が残日数（${rem}日）を超えています`;
    return e;
  }

  async function handleSubmit() {
    const e = validate();
    if (Object.keys(e).length) { setErrors(e); return; }
    setLoading(true);
    try {
      await new Promise(r => setTimeout(r, 600));
      onSubmit({ from: form.from, to: form.to || form.from, type: form.type, days: calcDays, reason: form.reason });
      setSent(true);
    } catch {
      setErrors({ submit: "送信に失敗しました。もう一度お試しください。" });
    } finally {
      setLoading(false);
    }
  }

  if (sent) return (
    <div className="bloom" style={{ display: "flex", flexDirection: "column", alignItems: "center", justifyContent: "center", minHeight: 360, gap: 18 }}>
      <div style={{ width: 72, height: 72, borderRadius: "50%", background: "rgba(110,231,183,0.1)", border: "1px solid rgba(110,231,183,0.3)", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 30, animation: "floatUp 2s ease-in-out infinite" }}>🌸</div>
      <p style={{ fontSize: 20, fontWeight: 700, color: "#F9FAFB" }}>申請を送信しました</p>
      <p style={{ fontSize: 13, color: "rgba(255,255,255,0.4)" }}>管理者が承認すると通知が届きます</p>
      <button onClick={() => { setSent(false); setForm({ from: "", to: "", type: "full", reason: "" }); setErrors({}); }}
        style={{ background: "rgba(255,255,255,0.06)", border: "1px solid rgba(255,255,255,0.1)", color: "rgba(255,255,255,0.5)", padding: "9px 20px", borderRadius: 10, cursor: "pointer", fontSize: 13, fontFamily: "'Zen Kaku Gothic New',sans-serif" }}>
        新しい申請をする
      </button>
    </div>
  );

  return (
    <div className="fade-up">
      <div style={{ marginBottom: 24 }}>
        <h1 style={{ fontSize: 20, fontWeight: 700, color: "#F9FAFB", marginBottom: 4 }}>有給申請</h1>
        <p style={{ fontSize: 13, color: "rgba(255,255,255,0.35)" }}>残日数：<span style={{ color: "#F9A8D4", fontWeight: 700, fontFamily: "'DM Mono'" }}>{rem}日</span> 利用可能</p>
      </div>

      <GlassCard style={{ maxWidth: 520 }}>
        {errors.submit && (
          <div style={{ background: "rgba(253,164,175,0.1)", border: "1px solid rgba(253,164,175,0.3)", borderRadius: 10, padding: "10px 14px", marginBottom: 18, fontSize: 13, color: "#FDA4AF" }}>{errors.submit}</div>
        )}

        {/* 休暇タイプ */}
        <div style={{ marginBottom: 20 }}>
          <p style={{ fontSize: 11, color: "rgba(255,255,255,0.35)", marginBottom: 10, letterSpacing: "0.07em" }}>休暇タイプ</p>
          <div style={{ display: "flex", gap: 8 }}>
            {[["full","終日休暇","1日"],["am","午前休","0.5日"],["pm","午後休","0.5日"]].map(([v,label,sub]) => (
              <button key={v} onClick={() => { setForm(f => ({ ...f, type: v, to: "" })); setErrors(p => ({ ...p, days: "" })); }} style={{
                flex: 1, padding: "10px 8px", borderRadius: 12, cursor: "pointer",
                background: form.type === v ? "rgba(249,168,212,0.12)" : "rgba(255,255,255,0.03)",
                border: `1px solid ${form.type === v ? "rgba(249,168,212,0.4)" : "rgba(255,255,255,0.07)"}`,
                color: form.type === v ? "#F9A8D4" : "rgba(255,255,255,0.35)",
                fontSize: 12, fontWeight: form.type === v ? 700 : 400,
                fontFamily: "'Zen Kaku Gothic New',sans-serif", transition: "all 0.15s",
              }}>
                <div>{label}</div><div style={{ fontSize: 10, marginTop: 2, opacity: 0.7 }}>{sub}</div>
              </button>
            ))}
          </div>
        </div>

        {/* 日付 */}
        <div className="date-grid" style={{ display: "grid", gridTemplateColumns: form.type === "full" ? "1fr 1fr" : "1fr", gap: 12, marginBottom: 6 }}>
          {[
            { label: form.type === "full" ? "開始日" : "取得日", key: "from" },
            ...(form.type === "full" ? [{ label: "終了日", key: "to" }] : []),
          ].map(f => (
            <div key={f.key}>
              <p style={{ fontSize: 11, color: "rgba(255,255,255,0.35)", marginBottom: 7, letterSpacing: "0.07em" }}>{f.label}</p>
              <input type="date" className={`input-field ${errors[f.key] ? "error" : ""}`} value={form[f.key]}
                onChange={e => { setForm(p => ({ ...p, [f.key]: e.target.value })); setErrors(p => ({ ...p, [f.key]: "", days: "" })); }} />
              <FieldError msg={errors[f.key]} />
            </div>
          ))}
        </div>
        {errors.days && <p style={{ fontSize: 11, color: "#FDA4AF", marginBottom: 14 }}>⚠ {errors.days}</p>}

        {/* 理由テンプレ */}
        <div style={{ marginBottom: 20, marginTop: 10 }}>
          <p style={{ fontSize: 11, color: "rgba(255,255,255,0.35)", marginBottom: 10, letterSpacing: "0.07em" }}>理由・備考</p>
          <div style={{ display: "flex", flexWrap: "wrap", gap: 7, marginBottom: 10 }}>
            {REASON_TEMPLATES.map(t => (
              <button key={t} className={`template-chip ${form.reason === t ? "active" : ""}`}
                onClick={() => { setForm(f => ({ ...f, reason: f.reason === t ? "" : t })); setErrors(p => ({ ...p, reason: "" })); }}>
                {t}
              </button>
            ))}
          </div>
          <input type="text" className={`input-field ${errors.reason ? "error" : ""}`} value={form.reason}
            placeholder="または直接入力…"
            onChange={e => { setForm(f => ({ ...f, reason: e.target.value })); setErrors(p => ({ ...p, reason: "" })); }} />
          <FieldError msg={errors.reason} />
        </div>

        {/* 日数プレビュー */}
        <div style={{ background: calcDays ? "rgba(249,168,212,0.07)" : "rgba(255,255,255,0.03)", border: `1px solid ${calcDays ? "rgba(249,168,212,0.3)" : "rgba(255,255,255,0.07)"}`, borderRadius: 14, padding: "14px 18px", marginBottom: 22, transition: "all 0.25s" }}>
          <p style={{ fontSize: 11, color: "rgba(255,255,255,0.35)", marginBottom: 6 }}>申請日数（自動計算）</p>
          <p style={{ fontFamily: "'DM Mono',monospace", fontSize: 28, fontWeight: 700, color: calcDays ? "#F9A8D4" : "rgba(255,255,255,0.2)" }}>
            {calcDays ?? "—"}
            <span style={{ fontSize: 13, fontFamily: "'Zen Kaku Gothic New'", color: "rgba(255,255,255,0.35)", marginLeft: 4 }}>日</span>
          </p>
        </div>

        <button className="btn-sakura" disabled={loading} onClick={handleSubmit}>
          {loading ? "送信中…" : "申請する 🌸"}
        </button>
      </GlassCard>
    </div>
  );
}

/* ══════════════════════════════════════════
   カレンダー（同日複数人警告付き）
══════════════════════════════════════════ */
function CalendarView() {
  const [year, setYear] = useState(2025);
  const [month, setMonth] = useState(2);
  const [selected, setSelected] = useState(null);

  const { first, total } = useMemo(() => ({
    first: new Date(year, month, 1).getDay(),
    total: new Date(year, month + 1, 0).getDate(),
  }), [year, month]);

  const key = d => `${year}-${String(month + 1).padStart(2, "0")}-${String(d).padStart(2, "0")}`;
  const prev = () => month === 0 ? (setMonth(11), setYear(y => y - 1)) : setMonth(m => m - 1);
  const next = () => month === 11 ? (setMonth(0), setYear(y => y + 1)) : setMonth(m => m + 1);
  const today = new Date();
  const isToday = d => d === today.getDate() && month === today.getMonth() && year === today.getFullYear();

  // 同日複数人アラート
  const crowdedDays = useMemo(() => {
    return Object.entries(VACATION_MAP)
      .filter(([k, v]) => k.startsWith(`${year}-${String(month + 1).padStart(2, "0")}`) && v.length >= 3)
      .map(([k]) => parseInt(k.split("-")[2]));
  }, [year, month]);

  return (
    <div className="fade-up">
      <div style={{ marginBottom: 24 }}>
        <h1 style={{ fontSize: 20, fontWeight: 700, color: "#F9FAFB", marginBottom: 4 }}>チームカレンダー</h1>
        <p style={{ fontSize: 13, color: "rgba(255,255,255,0.35)" }}>誰がいつ休むかひと目でわかります</p>
      </div>

      {/* 同日複数人アラート */}
      {crowdedDays.length > 0 && (
        <div style={{ background: "rgba(253,164,175,0.07)", border: "1px solid rgba(253,164,175,0.25)", borderRadius: 14, padding: "13px 18px", marginBottom: 16, display: "flex", alignItems: "flex-start", gap: 10 }}>
          <span style={{ fontSize: 18, flexShrink: 0 }}>👥</span>
          <div>
            <p style={{ fontSize: 13, fontWeight: 700, color: "#FDA4AF", marginBottom: 3 }}>同日多人数休暇アラート</p>
            <p style={{ fontSize: 12, color: "rgba(255,255,255,0.4)" }}>
              {crowdedDays.map(d => `${month + 1}月${d}日`).join("・")} に3名以上が同時休暇の申請があります。人員配置をご確認ください。
            </p>
          </div>
        </div>
      )}

      <GlassCard>
        <div style={{ display: "flex", alignItems: "center", justifyContent: "space-between", marginBottom: 22 }}>
          <button onClick={prev} style={{ background: "rgba(255,255,255,0.05)", border: "1px solid rgba(255,255,255,0.08)", color: "#F9FAFB", width: 36, height: 36, borderRadius: 10, cursor: "pointer", fontSize: 16, display: "flex", alignItems: "center", justifyContent: "center" }}>‹</button>
          <span style={{ fontFamily: "'DM Mono',monospace", fontSize: 15, fontWeight: 500, color: "#F9FAFB" }}>{year}年 {month + 1}月</span>
          <button onClick={next} style={{ background: "rgba(255,255,255,0.05)", border: "1px solid rgba(255,255,255,0.08)", color: "#F9FAFB", width: 36, height: 36, borderRadius: 10, cursor: "pointer", fontSize: 16, display: "flex", alignItems: "center", justifyContent: "center" }}>›</button>
        </div>

        <div style={{ display: "grid", gridTemplateColumns: "repeat(7,1fr)", gap: 4, marginBottom: 6 }}>
          {DAYS_JP.map((d, i) => <div key={d} style={{ textAlign: "center", fontSize: 11, fontWeight: 600, padding: "5px 0", color: i === 0 ? "#FDA4AF" : i === 6 ? "#93C5FD" : "rgba(255,255,255,0.3)" }}>{d}</div>)}
        </div>

        <div style={{ display: "grid", gridTemplateColumns: "repeat(7,1fr)", gap: 4 }}>
          {Array.from({ length: first }).map((_, i) => <div key={`e${i}`} />)}
          {Array.from({ length: total }).map((_, i) => {
            const d = i + 1;
            const k = key(d);
            const vacs = VACATION_MAP[k] || [];
            const dow = (first + i) % 7;
            const sel = selected === k;
            const crowded = vacs.length >= 3;
            return (
              <div key={d} className="cal-day" onClick={() => setSelected(sel ? null : k)} style={{
                background: crowded ? "rgba(253,164,175,0.07)" : sel ? "rgba(249,168,212,0.1)" : vacs.length ? "rgba(255,255,255,0.03)" : "transparent",
                border: `1px solid ${crowded ? "rgba(253,164,175,0.3)" : sel ? "rgba(249,168,212,0.35)" : vacs.length ? "rgba(255,255,255,0.08)" : "rgba(255,255,255,0.04)"}`,
                borderRadius: 10, padding: "7px 5px", minHeight: 64,
              }}>
                <div style={{ fontSize: 12, fontWeight: isToday(d) ? 700 : 400, marginBottom: 4, display: "flex", alignItems: "center", gap: 2, color: isToday(d) ? "#F9A8D4" : dow === 0 ? "#FDA4AF" : dow === 6 ? "#93C5FD" : "rgba(255,255,255,0.4)" }}>
                  {isToday(d) && <span style={{ width: 4, height: 4, borderRadius: "50%", background: "#F9A8D4", display: "inline-block" }} />}
                  {crowded && <span style={{ fontSize: 8 }}>⚠</span>}
                  {d}
                </div>
                {vacs.slice(0, 2).map(v => (
                  <div key={v.empId} style={{ fontSize: 9, padding: "2px 4px", borderRadius: 5, marginBottom: 2, background: `${v.color}18`, color: v.color, fontWeight: 700, overflow: "hidden", textOverflow: "ellipsis", whiteSpace: "nowrap" }}>
                    {v.name.split(" ")[0]}{v.type !== "終日" ? `(${v.type})` : ""}
                  </div>
                ))}
                {vacs.length > 2 && <div style={{ fontSize: 9, color: "#FDA4AF", fontWeight: 700 }}>+{vacs.length - 2}人</div>}
              </div>
            );
          })}
        </div>

        {selected && VACATION_MAP[selected] && (
          <div style={{ marginTop: 20, paddingTop: 20, borderTop: "1px solid rgba(255,255,255,0.07)" }}>
            <p style={{ fontSize: 11, color: "rgba(255,255,255,0.35)", marginBottom: 12, letterSpacing: "0.06em" }}>{selected} の休暇</p>
            {VACATION_MAP[selected].map(v => {
              const emp = DEMO_USERS.find(e => e.id === v.empId);
              return emp ? (
                <div key={v.empId} style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 10 }}>
                  <Avatar emp={emp} size={32} />
                  <div>
                    <p style={{ fontSize: 13, color: "#F9FAFB", fontWeight: 600 }}>{emp.name}</p>
                    <p style={{ fontSize: 11, color: "rgba(255,255,255,0.35)" }}>{emp.dept} · {v.type}</p>
                  </div>
                </div>
              ) : null;
            })}
          </div>
        )}
      </GlassCard>
    </div>
  );
}

/* ══════════════════════════════════════════
   管理者画面
══════════════════════════════════════════ */
function Admin({ requests, onApprove, onReject }) {
  const [tab, setTab] = useState("requests");
  const pending = requests.filter(r => r.status === "pending").length;

  function exportCSV() {
    const header = "氏名,部署,付与日数,取得日数,半休回数,残日数,取得率,5日義務\n";
    const rows = DEMO_USERS.filter(u => u.role === "employee").map(e => {
      const total = e.used + e.halfUsed * 0.5;
      const rem = e.total - total;
      const pct = Math.round((total / e.total) * 100);
      const oblig = e.used >= 5 ? "達成" : "未達成";
      return `${e.name},${e.dept},${e.total},${e.used},${e.halfUsed},${rem},${pct}%,${oblig}`;
    }).join("\n");
    const blob = new Blob(["\uFEFF" + header + rows], { type: "text/csv;charset=utf-8;" });
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a"); a.href = url;
    a.download = `有給管理_${new Date().toISOString().slice(0,10)}.csv`; a.click();
    URL.revokeObjectURL(url);
  }

  return (
    <div className="fade-up">
      <div style={{ display: "flex", alignItems: "flex-start", justifyContent: "space-between", marginBottom: 24, flexWrap: "wrap", gap: 12 }}>
        <div>
          <h1 style={{ fontSize: 20, fontWeight: 700, color: "#F9FAFB", marginBottom: 4 }}>管理者画面</h1>
          <p style={{ fontSize: 13, color: "rgba(255,255,255,0.35)" }}>全社員の有給管理・申請承認</p>
        </div>
        <button onClick={exportCSV} style={{ display: "flex", alignItems: "center", gap: 7, padding: "9px 18px", borderRadius: 11, cursor: "pointer", background: "rgba(110,231,183,0.08)", border: "1px solid rgba(110,231,183,0.25)", color: "#6EE7B7", fontSize: 13, fontWeight: 700, fontFamily: "'Zen Kaku Gothic New',sans-serif", transition: "all 0.15s" }}>
          ↓ CSVエクスポート
        </button>
      </div>

      <div style={{ display: "flex", gap: 4, marginBottom: 20, background: "rgba(255,255,255,0.03)", padding: 4, borderRadius: 13, width: "fit-content", border: "1px solid rgba(255,255,255,0.06)" }}>
        {[["requests","申請一覧",pending],["employees","社員一覧",null]].map(([id,label,badge]) => (
          <button key={id} onClick={() => setTab(id)} className="tab-btn" style={{ display: "flex", alignItems: "center", gap: 6, padding: "8px 18px", borderRadius: 10, border: "none", cursor: "pointer", background: tab === id ? "rgba(255,255,255,0.07)" : "transparent", color: tab === id ? "#F9FAFB" : "rgba(255,255,255,0.35)", fontSize: 13, fontWeight: tab === id ? 600 : 400 }}>
            {label}
            {badge > 0 && <span style={{ background: "#F9A8D4", color: "#1a0010", fontSize: 10, fontWeight: 800, borderRadius: 99, padding: "1px 6px" }}>{badge}</span>}
          </button>
        ))}
      </div>

      {tab === "requests" && (
        <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
          {requests.map(r => {
            const emp = DEMO_USERS.find(e => e.id === r.empId);
            return (
              <GlassCard key={r.id} style={{ padding: "16px 20px" }}>
                <div className="req-row" style={{ display: "flex", alignItems: "center", gap: 12 }}>
                  {emp && <Avatar emp={emp} size={42} />}
                  <div style={{ flex: 1, minWidth: 0 }}>
                    <div style={{ display: "flex", alignItems: "center", gap: 8, flexWrap: "wrap", marginBottom: 4 }}>
                      <span style={{ fontSize: 14, fontWeight: 700, color: "#F9FAFB" }}>{r.empName}</span>
                      <span style={{ fontSize: 10, color: "rgba(255,255,255,0.35)", background: "rgba(255,255,255,0.05)", padding: "2px 8px", borderRadius: 99, border: "1px solid rgba(255,255,255,0.08)" }}>{r.dept}</span>
                      {r.type !== "full" && <span style={{ fontSize: 10, padding: "2px 8px", borderRadius: 99, background: "rgba(249,168,212,0.1)", color: "#F9A8D4", border: "1px solid rgba(249,168,212,0.2)", fontWeight: 700 }}>{r.type === "am" ? "午前休" : "午後休"}</span>}
                    </div>
                    <p style={{ fontSize: 12, color: "rgba(255,255,255,0.35)" }}>{r.from}〜{r.to} · {r.days}日 · {r.reason}</p>
                  </div>
                  <div className="req-actions" style={{ display: "flex", alignItems: "center", gap: 8, flexShrink: 0 }}>
                    <StatusBadge status={r.status} />
                    {r.status === "pending" && (
                      <><button className="btn-sm-approve" onClick={() => onApprove(r.id)}>承認</button><button className="btn-sm-reject" onClick={() => onReject(r.id)}>却下</button></>
                    )}
                  </div>
                </div>
              </GlassCard>
            );
          })}
        </div>
      )}

      {tab === "employees" && (
        <div className="emp-grid" style={{ display: "grid", gridTemplateColumns: "repeat(2,1fr)", gap: 12 }}>
          {DEMO_USERS.filter(u => u.role === "employee").map(emp => {
            const totalUsed = emp.used + emp.halfUsed * 0.5;
            const rem = emp.total - totalUsed;
            const pct = Math.round((totalUsed / emp.total) * 100);
            const warn = rem <= 3;
            const obligOk = emp.used >= 5;
            return (
              <GlassCard key={emp.id} style={{ padding: "18px 20px" }}>
                <div style={{ display: "flex", alignItems: "center", gap: 12, marginBottom: 14 }}>
                  <Avatar emp={emp} size={42} />
                  <div style={{ flex: 1 }}>
                    <p style={{ fontSize: 14, fontWeight: 700, color: "#F9FAFB" }}>{emp.name}</p>
                    <p style={{ fontSize: 11, color: "rgba(255,255,255,0.35)" }}>{emp.dept}</p>
                  </div>
                  <div style={{ textAlign: "right" }}>
                    <p style={{ fontFamily: "'DM Mono',monospace", fontSize: 22, fontWeight: 700, color: warn ? "#FDA4AF" : emp.color }}>{rem}</p>
                    <p style={{ fontSize: 10, color: "rgba(255,255,255,0.3)" }}>残日数</p>
                  </div>
                </div>
                <div style={{ height: 4, background: "rgba(255,255,255,0.06)", borderRadius: 99, overflow: "hidden", marginBottom: 8 }}>
                  <div style={{ height: "100%", width: `${pct}%`, background: pct >= 80 ? "linear-gradient(90deg,#FCD34D,#FDA4AF)" : `linear-gradient(90deg,${emp.color}88,${emp.color})`, borderRadius: 99, transition: "width 0.7s ease" }} />
                </div>
                <div style={{ display: "flex", justifyContent: "space-between", fontSize: 10, color: "rgba(255,255,255,0.25)", marginBottom: 8 }}>
                  <span>取得 {totalUsed}日（半休 {emp.halfUsed}回）</span><span>付与 {emp.total}日</span>
                </div>
                <div style={{ display: "flex", gap: 6, flexWrap: "wrap" }}>
                  {warn && <span style={{ fontSize: 10, padding: "2px 8px", borderRadius: 99, background: "rgba(253,164,175,0.1)", color: "#FDA4AF", border: "1px solid rgba(253,164,175,0.2)" }}>残日数少</span>}
                  <span style={{ fontSize: 10, padding: "2px 8px", borderRadius: 99, background: obligOk ? "rgba(110,231,183,0.1)" : "rgba(252,211,77,0.1)", color: obligOk ? "#6EE7B7" : "#FCD34D", border: `1px solid ${obligOk ? "rgba(110,231,183,0.2)" : "rgba(252,211,77,0.2)"}` }}>
                    5日義務 {obligOk ? "✓" : `${emp.used}/5日`}
                  </span>
                </div>
              </GlassCard>
            );
          })}
        </div>
      )}
    </div>
  );
}

/* ══════════════════════════════════════════
   メインアプリ
══════════════════════════════════════════ */
export default function App() {
  const [currentUser, setCurrentUser] = useState(null);
  const [view, setView] = useState("dashboard");
  const [requests, setRequests] = useState(INIT_REQUESTS);
  const [showNotif, setShowNotif] = useState(false);
  const { toasts, addToast } = useToast();

  const unreadCount = currentUser ? requests.filter(r => r.empId === currentUser.id && !r.readByEmp && r.status !== "pending").length : 0;

  function handleLogin(user) { setCurrentUser(user); setView("dashboard"); }
  function handleLogout() { setCurrentUser(null); setView("dashboard"); }

  function handleApprove(id) {
    setRequests(r => r.map(x => x.id === id ? { ...x, status: "approved" } : x));
    addToast("申請を承認しました", "success");
  }
  function handleReject(id) {
    setRequests(r => r.map(x => x.id === id ? { ...x, status: "rejected" } : x));
    addToast("申請を却下しました", "error");
  }
  function handleSubmit(formData) {
    const newReq = { id: Date.now(), empId: currentUser.id, empName: currentUser.name, dept: currentUser.dept, ...formData, status: "pending", readByEmp: true };
    setRequests(r => [newReq, ...r]);
    addToast("申請を送信しました 🌸", "info");
  }
  function handleReadNotif(id) {
    setRequests(r => r.map(x => x.id === id ? { ...x, readByEmp: true } : x));
  }

  const NAV = [
    { id: "dashboard", icon: "🏠", label: "ホーム" },
    { id: "apply",     icon: "🌸", label: "申請" },
    { id: "calendar",  icon: "📅", label: "カレンダー" },
    ...(currentUser?.role === "admin" ? [{ id: "admin", icon: "⚙️", label: "管理" }] : []),
  ];

  if (!currentUser) return <LoginScreen onLogin={handleLogin} />;

  return (
    <div style={{ fontFamily: "'Zen Kaku Gothic New',sans-serif", minHeight: "100vh", display: "flex", background: "linear-gradient(135deg,#0d0815 0%,#100a1a 40%,#0a0f1a 100%)", color: "#F9FAFB", position: "relative", overflow: "hidden" }}>
      <style>{CSS}</style>
      <Toast toasts={toasts} />

      {/* 背景オーブ */}
      <div style={{ position: "fixed", inset: 0, pointerEvents: "none", zIndex: 0 }}>
        <div style={{ position: "absolute", width: 600, height: 600, borderRadius: "50%", top: -200, right: -150, background: "radial-gradient(circle,rgba(249,168,212,0.06) 0%,transparent 70%)" }} />
        <div style={{ position: "absolute", width: 400, height: 400, borderRadius: "50%", bottom: -100, left: -100, background: "radial-gradient(circle,rgba(192,132,252,0.05) 0%,transparent 70%)" }} />
      </div>

      {/* サイドバー */}
      <aside className="sidebar" style={{ width: 220, flexShrink: 0, position: "sticky", top: 0, height: "100vh", display: "flex", flexDirection: "column", zIndex: 10, background: "rgba(255,255,255,0.02)", backdropFilter: "blur(20px)", borderRight: "1px solid rgba(255,255,255,0.06)", padding: "28px 0" }}>
        <div style={{ padding: "0 24px 26px", borderBottom: "1px solid rgba(255,255,255,0.06)" }}>
          <p style={{ fontSize: 14, fontWeight: 700, color: "#F9A8D4", letterSpacing: "0.1em", marginBottom: 2 }}>🌸 KYUUKA</p>
          <p style={{ fontSize: 10, color: "rgba(255,255,255,0.25)", letterSpacing: "0.06em" }}>有給管理システム</p>
        </div>
        <nav style={{ flex: 1, padding: "18px 10px" }}>
          {NAV.map(item => (
            <button key={item.id} className="nav-btn" onClick={() => setView(item.id)} style={{ display: "flex", alignItems: "center", gap: 10, width: "100%", padding: "11px 14px", marginBottom: 3, background: view === item.id ? "rgba(249,168,212,0.1)" : "transparent", border: `1px solid ${view === item.id ? "rgba(249,168,212,0.25)" : "transparent"}`, borderRadius: 12, cursor: "pointer", color: view === item.id ? "#F9A8D4" : "rgba(255,255,255,0.35)", fontSize: 13, fontWeight: view === item.id ? 700 : 400, textAlign: "left", fontFamily: "'Zen Kaku Gothic New',sans-serif" }}>
              <span style={{ fontSize: 15 }}>{item.icon}</span>{item.label}
            </button>
          ))}
        </nav>
        <div style={{ padding: "18px 14px", borderTop: "1px solid rgba(255,255,255,0.06)" }}>
          <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 12 }}>
            <Avatar emp={currentUser} size={36} />
            <div style={{ flex: 1, minWidth: 0 }}>
              <p style={{ fontSize: 12, fontWeight: 600, color: "#F9FAFB" }}>{currentUser.name}</p>
              <p style={{ fontSize: 10, color: "rgba(255,255,255,0.3)" }}>{currentUser.role === "admin" ? "👑 管理者" : currentUser.dept}</p>
            </div>
          </div>
          <button onClick={handleLogout} style={{ width: "100%", padding: "8px", background: "rgba(255,255,255,0.04)", border: "1px solid rgba(255,255,255,0.07)", borderRadius: 9, color: "rgba(255,255,255,0.35)", fontSize: 12, cursor: "pointer", fontFamily: "'Zen Kaku Gothic New',sans-serif" }}>ログアウト</button>
        </div>
      </aside>

      {/* メイン */}
      <main className="main-pad" style={{ flex: 1, padding: "36px 40px", overflowY: "auto", maxWidth: 840, position: "relative", zIndex: 1 }}>
        {/* 通知ベル */}
        <div style={{ position: "fixed", top: 20, right: 20, zIndex: 500 }}>
          <button onClick={() => setShowNotif(v => !v)} style={{ width: 42, height: 42, borderRadius: "50%", background: "rgba(255,255,255,0.06)", border: "1px solid rgba(255,255,255,0.1)", cursor: "pointer", fontSize: 18, display: "flex", alignItems: "center", justifyContent: "center", position: "relative", backdropFilter: "blur(10px)" }}>
            🔔
            {unreadCount > 0 && <span style={{ position: "absolute", top: -2, right: -2, width: 16, height: 16, borderRadius: "50%", background: "#F9A8D4", color: "#1a0010", fontSize: 9, fontWeight: 800, display: "flex", alignItems: "center", justifyContent: "center" }}>{unreadCount}</span>}
          </button>
          {showNotif && (
            <>
              <div style={{ position: "fixed", inset: 0, zIndex: 498 }} onClick={() => setShowNotif(false)} />
              <NotificationPanel requests={requests} currentUser={currentUser} onRead={handleReadNotif} onClose={() => setShowNotif(false)} />
            </>
          )}
        </div>

        {view === "dashboard" && <Dashboard emp={currentUser} requests={requests} />}
        {view === "apply"     && <Apply emp={currentUser} onSubmit={handleSubmit} />}
        {view === "calendar"  && <CalendarView />}
        {view === "admin"     && currentUser.role === "admin" && <Admin requests={requests} onApprove={handleApprove} onReject={handleReject} />}
        {view === "admin"     && currentUser.role !== "admin" && <div style={{ color: "#FDA4AF", padding: 40, textAlign: "center" }}>⚠ 管理者権限が必要です</div>}
      </main>

      {/* モバイルナビ */}
      <nav className="mobile-nav" style={{ position: "fixed", bottom: 0, left: 0, right: 0, zIndex: 100, background: "rgba(13,8,21,0.9)", backdropFilter: "blur(20px)", borderTop: "1px solid rgba(249,168,212,0.1)", display: "flex", justifyContent: "space-around", padding: "10px 0 16px" }}>
        {NAV.map(item => (
          <button key={item.id} onClick={() => setView(item.id)} style={{ display: "flex", flexDirection: "column", alignItems: "center", gap: 4, background: "none", border: "none", cursor: "pointer", color: view === item.id ? "#F9A8D4" : "rgba(255,255,255,0.3)", fontFamily: "'Zen Kaku Gothic New',sans-serif", transition: "color 0.15s" }}>
            <span style={{ fontSize: 20 }}>{item.icon}</span>
            <span style={{ fontSize: 10, fontWeight: view === item.id ? 700 : 400 }}>{item.label}</span>
          </button>
        ))}
      </nav>
    </div>
  );
}

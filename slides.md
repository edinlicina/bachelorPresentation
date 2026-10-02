---
theme: default
title: Konzeption und Evaluierung moderner Authentifizierungsverfahren
info: |
  Bachelorarbeit – Moderne Authentifizierungsverfahren für Webanwendungen
class: text-center
transition: slide-left
mdc: true
---

<!-- ===================================================== -->
<!-- FOLIE 1 – TITEL                                       -->
<!-- ===================================================== -->

<div class="title-slide">

<div class="eyebrow">
BACHELORARBEIT · IKT
</div>

# Moderne

# Authentifizierung.

<div class="title-accent"></div>

<p class="subtitle">
Konzeption und Evaluierung moderner Authentifizierungsverfahren
für Webanwendungen
</p>

<div class="auth-methods">
  <span>TOTP</span>
  <span class="separator">/</span>
  <span>PASSKEYS</span>
  <span class="separator">/</span>
  <span>FIDO2</span>
</div>

<div class="author">
Edin Licina
</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 2 – MOTIVATION                                  -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
01 / MOTIVATION
</div>

# Das Problem ist nicht

# nur das Passwort.

<p class="slide-lead">
Ein zusätzlicher Faktor bedeutet nicht automatisch
<span class="accent">Phishing-Resistenz.</span>
</p>

<div class="evolution-row">

<div v-click class="concept-card">

<span class="card-index">01</span>

<div class="card-icon">
••••••••
</div>

<h3>Passwort</h3>

<p>
Wiederverwendbares Geheimnis
</p>

</div>

<div v-click class="connector">
<span>+</span>
</div>

<div v-click class="concept-card">

<span class="card-index">02</span>

<div class="card-icon">
483 921
</div>

<h3>TOTP</h3>

<p>
Zweiter Faktor
</p>

</div>

<div v-click class="connector">
<span>≠</span>
</div>

<div v-click class="concept-card danger-card">

<span class="card-index">03</span>

<div class="card-icon">
PHISHING
</div>

<h3>Phishing-resistent?</h3>

<p>
Nein – Codes können weitergeleitet werden.
</p>

</div>

</div>

<div v-click class="takeaway">
MFA erhöht die Sicherheit.
<strong>
Das zugrunde liegende Phishing-Problem bleibt jedoch bestehen.
</strong>
</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 3 – PARADIGMENWECHSEL                           -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
02 / STAND DER TECHNIK
</div>

# Vom Shared Secret

# zum Public Key.

<p class="slide-lead">
Moderne Authentifizierung fügt nicht nur einen Faktor hinzu —
<span class="accent">sie verändert das Sicherheitsmodell.</span>
</p>

<div class="paradigm">

<div v-click class="paradigm-stage">

<div class="stage-label">01 / PASSWORD</div>

<div class="stage-visual">
SECRET
</div>

<h3>Passwort</h3>

<p>
Ein wiederverwendbares Geheimnis bildet die Grundlage
der Authentifizierung.
</p>

</div>

<div v-click class="paradigm-arrow">
→
</div>

<div v-click class="paradigm-stage">

<div class="stage-label">02 / MFA</div>

<div class="stage-visual">
SECRET + OTP
</div>

<h3>Passwort + TOTP</h3>

<p>
Ein zusätzlicher Faktor erhöht die Sicherheit,
bleibt aber Shared-Secret-basiert.
</p>

</div>

<div v-click class="paradigm-arrow paradigm-break">
→
</div>

<div v-click class="paradigm-stage public-stage">

<div class="stage-label">
03 / PUBLIC KEY
</div>

<div class="keypair">

<span class="private-key">
PRIVATE
</span>

<span class="key-separator">
↔
</span>

<span class="public-key">
PUBLIC
</span>

</div>

<h3>FIDO2 / WebAuthn</h3>

<p>
Asymmetrische Kryptographie ersetzt das
gemeinsame Authentifizierungsgeheimnis.
</p>

</div>

</div>

<div v-click class="paradigm-takeaway">

<div>
<span class="mini-label">AUTHENTICATOR</span>
<strong>Private Key</strong>
bleibt beim Authenticator
</div>

<div class="takeaway-divider"></div>

<div>
<span class="mini-label">SERVER</span>
<strong>Public Key</strong>
wird zur Verifikation gespeichert
</div>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 4 – UNTERSUCHUNGSGEGENSTAND                     -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
03 / SCOPE
</div>

# Drei Strategien.

# Zwei Sicherheitsmodelle.

<p class="slide-lead">
Alle Varianten werden innerhalb
<span class="accent">derselben Webanwendung</span>
implementiert.
</p>

<div class="strategy-grid">

<div v-click class="strategy">

<div class="strategy-top">

<span class="strategy-id">
01
</span>

<span class="strategy-type">
SHARED SECRET
</span>

</div>

<div class="strategy-symbol">
483 921
</div>

<h3>
Passwort + TOTP
</h3>

<p>
Passwortbasierte Anmeldung mit
zeitbasiertem zweiten Faktor.
</p>

<div class="strategy-bottom">
RFC 6238
</div>

</div>

<div v-click class="strategy strategy-public">

<div class="strategy-top">

<span class="strategy-id">
02
</span>

<span class="strategy-type public">
PUBLIC KEY
</span>

</div>

<div class="strategy-symbol">
PASSKEY
</div>

<h3>
Synced Passkey
</h3>

<p>
WebAuthn-Credential mit
geräteübergreifender Verfügbarkeit.
</p>

<div class="strategy-bottom">
WEBAUTHN
</div>

</div>

<div v-click class="strategy strategy-public">

<div class="strategy-top">

<span class="strategy-id">
03
</span>

<span class="strategy-type public">
PUBLIC KEY
</span>

</div>

<div class="strategy-symbol">
USB / NFC
</div>

<h3>
Security Key
</h3>

<p>
Hardwaregebundenes Credential
auf einem externen Authenticator.
</p>

<div class="strategy-bottom">
WEBAUTHN / FIDO2
</div>

</div>

</div>

<div v-click class="scope-footer">

<span>GLEICHE ANWENDUNG</span>

<span class="scope-arrow">
→
</span>

<span>GLEICHE RAHMENBEDINGUNGEN</span>

<span class="scope-arrow">
→
</span>

<strong>
VERGLEICHBARE EVALUATION
</strong>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 5 – BEDROHUNGSMODELL                            -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
04 / BEDROHUNGSMODELL
</div>

# „Sicher“ ist keine

# messbare Eigenschaft.

<p class="slide-lead">
Deshalb wird Sicherheit in
<span class="accent">konkrete Angriffsszenarien und Eigenschaften</span>
zerlegt.
</p>

<div class="threat-layout">

<div class="threat-list">

<div v-click class="threat">

<span class="threat-code">
T01
</span>

<div>
<strong>Phishing</strong>
<p>
Credential Capture durch einen falschen Verifier.
</p>
</div>

</div>

<div v-click class="threat">

<span class="threat-code">
T02
</span>

<div>
<strong>Adversary-in-the-Middle</strong>
<p>
Echtzeit-Weiterleitung gültiger Authentifizierungsdaten.
</p>
</div>

</div>

<div v-click class="threat">

<span class="threat-code">
T03
</span>

<div>
<strong>Replay</strong>
<p>
Wiederverwendung aufgezeichneter Authentifizierungsdaten.
</p>
</div>

</div>

<div v-click class="threat">

<span class="threat-code">
T04
</span>

<div>
<strong>Server Compromise</strong>
<p>
Auswirkungen kompromittierter Credential-Daten.
</p>
</div>

</div>

<div v-click class="threat">

<span class="threat-code">
T05
</span>

<div>
<strong>Credential Loss</strong>
<p>
Verlust, Widerruf und Wiederherstellung.
</p>
</div>

</div>

</div>

<div v-click class="security-definition">

<div class="definition-label">
SECURITY MODEL
</div>

<div class="definition-main">

Nicht

<span>
„Wie sicher ist es?“
</span>

</div>

<div class="definition-divider"></div>

<div class="definition-main positive">

Sondern

<span>
„Wogegen schützt es?“
</span>

</div>

<div class="definition-footnote">
Definierte Eigenschaften statt subjektiver Gesamtscore
</div>

</div>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 6 – TOTP FUNKTIONSWEISE                         -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
05 / TOTP
</div>

# Ein Secret.

# Zwei Berechnungen.

<p class="slide-lead">
TOTP erzeugt aus einem gemeinsamen Secret und der Zeit
<span class="accent">kurzlebige Einmalcodes.</span>
</p>

<div class="totp-flow">

<div v-click class="totp-node">
  <div class="node-label">AUTHENTICATOR</div>
  <div class="node-title">Smartphone</div>
  <div class="node-secret">K = SECRET</div>
</div>

<div v-click class="totp-operation">
  <span class="operation-input">K + TIME</span>
  <span class="operation-arrow">→</span>
  <span class="operation-box">HMAC</span>
</div>

<div v-click class="totp-code">
  <div class="code-label">TOTP</div>
  <div class="code-value">483 921</div>
  <div class="code-life">
    <span></span>
    ~30 s
  </div>
</div>

<div v-click class="totp-operation reverse">
  <span class="operation-box">VERIFY</span>
  <span class="operation-arrow">→</span>
  <span class="operation-input">K + TIME</span>
</div>

<div v-click class="totp-node server-node">
  <div class="node-label">SERVER</div>
  <div class="node-title">Verifier</div>
  <div class="node-secret">K = SECRET</div>
</div>

</div>

<div v-click class="formula-strip">

<span class="formula-name">RFC 6238</span>

<span class="formula">
TOTP = HOTP(K, T)
</span>

<span class="formula-divider"></span>

<span class="formula">
T = ⌊ (CurrentTime − T₀) / X ⌋
</span>

</div>

<div v-click class="technical-takeaway">
  <span>WICHTIG</span>
  Authenticator und Server benötigen Informationen über
  <strong>dasselbe Secret K.</strong>
</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 7 – TOTP PHISHING                               -->
<!-- ===================================================== -->

<div class="content-slide phishing-slide">

<div class="slide-kicker">
06 / REAL-TIME PHISHING
</div>

# 30 Sekunden reichen.

# Dem Angreifer auch.

<p class="slide-lead">
Der Code ist kurzlebig —
<span class="accent">aber nicht an den legitimen Dienst gebunden.</span>
</p>

<div class="attack-flow">

<div v-click class="attack-actor user-actor">
  <div class="actor-symbol">USER</div>
  <strong>Benutzer</strong>
  <span>sieht gefälschten Login</span>
</div>

<div v-click class="attack-channel">
  <div class="channel-data">
    PASSWORD
    <span>+</span>
    483 921
  </div>
  <div class="channel-arrow danger-line">→</div>
</div>

<div v-click class="attack-actor attacker-actor">
  <div class="actor-symbol danger-symbol">FAKE</div>
  <strong>Phishing Site</strong>
  <span>evil-example.com</span>
</div>

<div v-click class="attack-channel">
  <div class="channel-data">
    REAL-TIME
    <span>FORWARD</span>
  </div>
  <div class="channel-arrow danger-line">→</div>
</div>

<div v-click class="attack-actor server-actor">
  <div class="actor-symbol">RP</div>
  <strong>Echter Dienst</strong>
  <span>example.com</span>
</div>

</div>

<div v-click class="attack-result">

<div class="attack-result-left">
  <span class="result-label">RESULT</span>
  <strong>Credential akzeptiert</strong>
</div>

<div class="result-status">
  LOGIN
  <span>✓</span>
</div>

</div>

<div v-click class="attack-insight">
  <span>Das Problem:</span>
  <strong>483 921</strong> weiß nicht, für welche Website der Code eingegeben wurde.
</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 8 – WEBAUTHN ARCHITEKTUR                        -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
07 / FIDO2 + WEBAUTHN
</div>

# Kein Shared Secret

# mit dem Server.

<p class="slide-lead">
WebAuthn verwendet
<span class="accent">asymmetrische Kryptographie</span>
und trennt Private Key und Public Key.
</p>

<div class="webauthn-architecture">

<div v-click class="wa-party">
  <div class="wa-number">01</div>
  <div class="wa-icon">RP</div>
  <h3>Relying Party</h3>
  <p>Webanwendung / Backend</p>
</div>

<div v-click class="wa-link">
  <span>CHALLENGE</span>
  <div>→</div>
</div>

<div v-click class="wa-party client-party">
  <div class="wa-number">02</div>
  <div class="wa-icon">WEB</div>
  <h3>Client</h3>
  <p>Browser + WebAuthn API</p>
</div>

<div v-click class="wa-link">
  <span>CTAP / PLATFORM</span>
  <div>→</div>
</div>

<div v-click class="wa-party authenticator-party">
  <div class="wa-number">03</div>
  <div class="wa-icon key-icon">PRIVATE</div>
  <h3>Authenticator</h3>
  <p>verwendet den privaten Schlüssel</p>
</div>

</div>

<div v-click class="key-separation">

<div class="key-location private-location">
  <span class="location-label">AUTHENTICATOR</span>
  <strong>Private Key</strong>
  <small>bleibt unter Kontrolle des Authenticators</small>
</div>

<div class="key-separation-line">
  ≠
</div>

<div class="key-location public-location">
  <span class="location-label">SERVER</span>
  <strong>Public Key</strong>
  <small>verifiziert kryptographische Assertions</small>
</div>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 9 – WEBAUTHN REGISTRATION                       -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
08 / WEBAUTHN REGISTRATION
</div>

# Das Credential

# entsteht beim Registrieren.

<p class="slide-lead">
Der Server erhält den Public Key.
<span class="accent">Der Private Key bleibt beim Authenticator.</span>
</p>

<div class="ceremony">

<div class="ceremony-column">
  <div class="ceremony-head">BROWSER</div>

  <div v-click class="ceremony-event">
    <span class="event-number">01</span>
    Registrierung starten
  </div>

  <div v-click class="ceremony-code">
    navigator.credentials.create()
  </div>
</div>

<div class="ceremony-center">

<div v-click class="ceremony-message message-right">
  <span>registration request</span>
  →
</div>

<div v-click class="ceremony-message message-left">
  ←
  <span>challenge + options</span>
</div>

<div v-click class="ceremony-message message-right accent-message">
  <span>public credential data</span>
  →
</div>

</div>

<div class="ceremony-column">
  <div class="ceremony-head">SERVER</div>

  <div v-click class="ceremony-event server-event">
    <span class="event-number">02</span>
    Challenge erzeugen
  </div>

  <div v-click class="ceremony-event server-event">
    <span class="event-number">04</span>
    Public Key speichern
  </div>
</div>

<div v-click class="authenticator-popout">

<div class="auth-pop-label">
AUTHENTICATOR
</div>

<div class="auth-pop-main">
<span>03</span>
Schlüsselpaar erzeugen
</div>

<div class="generated-keys">

<div>
  <span class="key-tag private-tag">PRIVATE</span>
  <strong>bleibt hier</strong>
</div>

<div>
  <span class="key-tag public-tag">PUBLIC</span>
  <strong>→ Server</strong>
</div>

</div>

</div>

</div>

<div v-click class="ceremony-summary">
  <span>REGISTRATION RESULT</span>
  Server besitzt <strong>keinen Private Key.</strong>
</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 10 – WEBAUTHN AUTHENTICATION                    -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
09 / WEBAUTHN AUTHENTICATION
</div>

# Challenge.

# Signatur. Verifikation.

<p class="slide-lead">
Der Private Key wird nicht übertragen —
<span class="accent">er beweist seinen Besitz durch eine Signatur.</span>
</p>

<div class="auth-sequence">

<div v-click class="sequence-step">
  <span class="sequence-number">01</span>
  <div class="sequence-entity">SERVER</div>
  <div class="sequence-content">
    <strong>Challenge erzeugen</strong>
    <code>random challenge</code>
  </div>
</div>

<div v-click class="sequence-line"></div>

<div v-click class="sequence-step">
  <span class="sequence-number">02</span>
  <div class="sequence-entity">BROWSER</div>
  <div class="sequence-content">
    <strong>Credential anfordern</strong>
    <code>navigator.credentials.get()</code>
  </div>
</div>

<div v-click class="sequence-line"></div>

<div v-click class="sequence-step highlighted-step">
  <span class="sequence-number">03</span>
  <div class="sequence-entity">AUTHENTICATOR</div>
  <div class="sequence-content">
    <strong>Assertion signieren</strong>
    <code>Sign(data, privateKey)</code>
  </div>
</div>

<div v-click class="sequence-line"></div>

<div v-click class="sequence-step">
  <span class="sequence-number">04</span>
  <div class="sequence-entity">SERVER</div>
  <div class="sequence-content">
    <strong>Assertion verifizieren</strong>
    <code>Verify(data, publicKey)</code>
  </div>
</div>

</div>

<div v-click class="verification-row">

<div class="verify-item">
  <span>✓</span>
  Challenge
</div>

<div class="verify-item">
  <span>✓</span>
  Origin
</div>

<div class="verify-item">
  <span>✓</span>
  RP ID
</div>

<div class="verify-item">
  <span>✓</span>
  Signature
</div>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 11 – WEBAUTHN PHISHING RESISTANCE               -->
<!-- ===================================================== -->

<div class="content-slide phishing-slide">

<div class="slide-kicker">
10 / VERIFIER BINDING
</div>

# Gleicher Angriff.

# Anderes Ergebnis.

<p class="slide-lead">
WebAuthn-Credentials sind an den Kontext der
<span class="accent">Relying Party</span> gebunden.
</p>

<div class="comparison-attack">

<div v-click class="comparison-user">
  <div class="comparison-icon">USER</div>
  <strong>Benutzer</strong>
</div>

<div v-click class="comparison-arrow">
  →
</div>

<div v-click class="comparison-phish">
  <div class="comparison-domain">
    evil-example.com
  </div>

<strong>Phishing Site</strong>

  <div class="rp-mismatch">
    RP ID MISMATCH
  </div>
</div>

<div v-click class="blocked-path">

<div class="blocked-line"></div>

<div class="blocked-symbol">
×
</div>

<div class="blocked-line"></div>

</div>

<div v-click class="comparison-server">
  <div class="comparison-domain legit-domain">
    example.com
  </div>

<strong>Legitimer Dienst</strong>

</div>

</div>

<div v-click class="binding-explanation">

<div class="binding-credential">
  <span>CREDENTIAL</span>
  <strong>example.com</strong>
</div>

<div class="binding-arrow">
  ↕
</div>

<div class="binding-rp">
  <span>RP ID</span>
  <strong>example.com</strong>
</div>

</div>

<div v-click class="blocked-result">

<div>
  <span class="result-label">RESULT</span>
  <strong>Credential nicht für Phishing-Origin verwendbar</strong>
</div>

<div class="blocked-status">
  BLOCKED
  <span>×</span>
</div>

</div>

<div v-click class="final-security-message">
  Phishing-Resistenz entsteht nicht dadurch, dass der Benutzer besser aufpasst —
  <strong>sie wird durch das Protokoll unterstützt.</strong>
</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 12 – PASSKEYS                                   -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
11 / PASSKEYS
</div>

# WebAuthn.

# Aber alltagstauglich.

<p class="slide-lead">
Passkeys verwenden WebAuthn-Credentials, abstrahieren deren Nutzung jedoch
<span class="accent">stärker für den Endanwender.</span>
</p>

<div class="passkey-layout">

<div v-click class="passkey-device">

<div class="device-header">
  DEVICE
</div>

<div class="device-screen">

<div class="passkey-prompt">
  <span class="prompt-label">SIGN IN</span>

<strong>example.com</strong>

  <div class="biometric-symbol">
    ◎
  </div>

  <span class="prompt-action">
    Touch ID
  </span>
</div>

</div>

</div>

<div class="passkey-properties">

<div v-click class="passkey-property">

<span class="property-number">01</span>

<div>
  <strong>Kein Passwort eingeben</strong>
  <p>
    Authentifizierung erfolgt über ein kryptographisches Credential.
  </p>
</div>

</div>

<div v-click class="passkey-property">

<span class="property-number">02</span>

<div>
  <strong>Lokale Benutzerverifikation</strong>
  <p>
    Biometrie oder Geräte-PIN entsperrt die Nutzung des Credentials.
  </p>
</div>

</div>

<div v-click class="passkey-property">

<span class="property-number">03</span>

<div>
  <strong>Synchronisierbar</strong>
  <p>
    Multi-Device Passkeys können über ein Credential-Ökosystem
    auf mehreren Geräten verfügbar sein.
  </p>
</div>

</div>

</div>

</div>

<div v-click class="passkey-model">

<span class="model-label">
USER EXPERIENCE
</span>

<strong>
Gerät entsperren
</strong>

<span class="model-arrow">→</span>

<strong>
WebAuthn Assertion
</strong>

<span class="model-arrow">→</span>

<strong class="model-result">
Login
</strong>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 13 – SECURITY KEYS                              -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
12 / SECURITY KEYS
</div>

# Dasselbe Protokoll.

# Andere Credential-Strategie.

<p class="slide-lead">
Ein Security Key nutzt ebenfalls FIDO2/WebAuthn —
<span class="accent">das Credential bleibt jedoch an Hardware gebunden.</span>
</p>

<div class="security-key-layout">

<div v-click class="hardware-key">

<div class="usb-connector">
  <span></span>
  <span></span>
</div>

<div class="key-body">

<div class="key-led"></div>

<div class="key-touch">
  ◎
</div>

<div class="key-brand">
  FIDO2
</div>

</div>

</div>

<div class="hardware-properties">

<div v-click class="hardware-property">

<div class="hardware-property-top">
  <span>01</span>
  <strong>Hardwaregebunden</strong>
</div>

<p>
Credential verbleibt auf dem externen Authenticator.
</p>

</div>

<div v-click class="hardware-property">

<div class="hardware-property-top">
  <span>02</span>
  <strong>Portabel</strong>
</div>

<p>
Ein physischer Key kann an verschiedenen Geräten verwendet werden.
</p>

</div>

<div v-click class="hardware-property">

<div class="hardware-property-top">
  <span>03</span>
  <strong>Separater Besitzfaktor</strong>
</div>

<p>
Der Authenticator ist physisch vom Clientgerät getrennt.
</p>

</div>

</div>

</div>

<div v-click class="passkey-vs-key">

<div>
<span>PASSKEY</span>
<strong>Credential kann synchronisiert werden</strong>
</div>

<div class="versus-divider">
VS
</div>

<div>
<span>SECURITY KEY</span>
<strong>Credential bleibt auf dem Authenticator</strong>
</div>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 14 – TRADE-OFFS / RECOVERY                      -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
13 / TRADE-OFFS
</div>

# Sicherheit endet nicht

# beim Login.

<p class="slide-lead">
Ein Authentifizierungsverfahren muss auch
<span class="accent">Verlust, Recovery und Alltagstauglichkeit</span>
beherrschen.
</p>

<div class="tradeoff-grid">

<div v-click class="tradeoff-column">

<div class="tradeoff-header totp-header">
  <span>01</span>
  <strong>TOTP</strong>
</div>

<div class="tradeoff-row">
  <span>PHISHING</span>
  <strong class="tradeoff-warning">anfällig für Relay</strong>
</div>

<div class="tradeoff-row">
  <span>ONBOARDING</span>
  <strong>QR + Authenticator</strong>
</div>

<div class="tradeoff-row">
  <span>LOSS</span>
  <strong>Secret / Recovery nötig</strong>
</div>

<div class="tradeoff-row">
  <span>PORTABILITY</span>
  <strong>Authenticator-abhängig</strong>
</div>

</div>

<div v-click class="tradeoff-column featured-tradeoff">

<div class="tradeoff-header">
  <span>02</span>
  <strong>Synced Passkey</strong>
</div>

<div class="tradeoff-row">
  <span>PHISHING</span>
  <strong class="tradeoff-good">verifier-bound</strong>
</div>

<div class="tradeoff-row">
  <span>ONBOARDING</span>
  <strong>Geräteintegration</strong>
</div>

<div class="tradeoff-row">
  <span>LOSS</span>
  <strong>Sync / Ökosystem</strong>
</div>

<div class="tradeoff-row">
  <span>PORTABILITY</span>
  <strong>Multi-Device</strong>
</div>

</div>

<div v-click class="tradeoff-column">

<div class="tradeoff-header">
  <span>03</span>
  <strong>Security Key</strong>
</div>

<div class="tradeoff-row">
  <span>PHISHING</span>
  <strong class="tradeoff-good">verifier-bound</strong>
</div>

<div class="tradeoff-row">
  <span>ONBOARDING</span>
  <strong>Hardware registrieren</strong>
</div>

<div class="tradeoff-row">
  <span>LOSS</span>
  <strong>Backup-Key / Recovery</strong>
</div>

<div class="tradeoff-row">
  <span>PORTABILITY</span>
  <strong>physischer Key</strong>
</div>

</div>

</div>

<div v-click class="tradeoff-question">

<span>
DIE EIGENTLICHE FRAGE
</span>

<strong>
Welcher Trade-off ist für eine konkrete Webanwendung angemessen?
</strong>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 15 – STAND DER TECHNIK / RESEARCH GAP           -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
14 / STAND DER TECHNIK
</div>

# Die Technologien existieren.

# Die Entscheidung bleibt.

<p class="slide-lead">
Standards definieren die Verfahren sehr genau —
<span class="accent">aber nicht die optimale Strategie für jeden Anwendungskontext.</span>
</p>

<div class="research-landscape">

<div v-click class="research-source">

<div class="source-top">
  <span class="source-number">01</span>
  <span class="source-type">STANDARD</span>
</div>

<div class="source-name">
RFC 6238
</div>

<strong>
TOTP
</strong>

<p>
Definiert die zeitbasierte Erzeugung
von One-Time Passwords.
</p>

</div>

<div v-click class="research-source">

<div class="source-top">
  <span class="source-number">02</span>
  <span class="source-type">STANDARD</span>
</div>

<div class="source-name">
W3C
</div>

<strong>
WebAuthn
</strong>

<p>
Definiert die Web-API und das
Public-Key-Credential-Modell.
</p>

</div>

<div v-click class="research-source">

<div class="source-top">
  <span class="source-number">03</span>
  <span class="source-type">SPECIFICATION</span>
</div>

<div class="source-name">
FIDO ALLIANCE
</div>

<strong>
FIDO2 / CTAP
</strong>

<p>
Beschreibt die Kommunikation und
Authentifizierung mit FIDO-Authenticators.
</p>

</div>

</div>

<div v-click class="known-vs-open">

<div class="known-side">

<span class="knowledge-label">
BEKANNT
</span>

<strong>
Wie die Verfahren technisch funktionieren
</strong>

<div class="knowledge-items">
  <span>Protokolle</span>
  <span>Kryptographie</span>
  <span>Standards</span>
</div>

</div>

<div class="research-gap-symbol">
?
</div>

<div class="open-side">

<span class="knowledge-label accent-label">
BEITRAG DER ARBEIT
</span>

<strong>
Wie unterscheiden sie sich unter denselben praktischen Rahmenbedingungen?
</strong>

<div class="knowledge-items">
  <span>Sicherheit</span>
  <span>Usability</span>
  <span>Implementierung</span>
  <span>Recovery</span>
</div>

</div>

</div>

<div v-click class="transition-question">
Damit ergibt sich die
<strong>Forschungsfrage.</strong>
</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 16 – FORSCHUNGSFRAGE                            -->
<!-- ===================================================== -->

<div class="question-slide">

<div class="question-kicker">
15 / FORSCHUNGSFRAGE
</div>

<div class="question-prefix">
Wie unterscheiden sich
</div>

<h1>
Passwort + TOTP,<br>
<span>synced Passkeys</span> und<br>
hardwaregebundene Security Keys
</h1>

<div class="question-suffix">
hinsichtlich
<strong>Sicherheit, Usability, Recovery und Implementierungsaufwand</strong>
bei der Authentifizierung in einer Webanwendung?
</div>

<div v-click class="question-focus">

<div>
  <span>01</span>
  SICHERHEIT
</div>

<div>
  <span>02</span>
  USABILITY
</div>

<div>
  <span>03</span>
  RECOVERY
</div>

<div>
  <span>04</span>
  IMPLEMENTIERUNG
</div>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 17 – BEWERTUNGSKRITERIEN                        -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
16 / EVALUATION FRAMEWORK
</div>

# Vier Perspektiven.

# Ein Vergleich.

<p class="slide-lead">
Die Forschungsfrage wird in
<span class="accent">beobachtbare und dokumentierbare Kriterien</span>
zerlegt.
</p>

<div class="criteria-grid">

<div v-click class="criterion-card">

<div class="criterion-number">01</div>

<div class="criterion-icon">
SEC
</div>

<h3>Sicherheit</h3>

<div class="criterion-items">
  <span>Phishing / Relay</span>
  <span>Replay</span>
  <span>Verifier Binding</span>
  <span>Server Compromise</span>
</div>

</div>

<div v-click class="criterion-card">

<div class="criterion-number">02</div>

<div class="criterion-icon">
UX
</div>

<h3>Usability</h3>

<div class="criterion-items">
  <span>Registrierung</span>
  <span>Login-Schritte</span>
  <span>Gerätewechsel</span>
  <span>Fehlerszenarien</span>
</div>

</div>

<div v-click class="criterion-card">

<div class="criterion-number">03</div>

<div class="criterion-icon">
REC
</div>

<h3>Recovery</h3>

<div class="criterion-items">
  <span>Credential-Verlust</span>
  <span>Backup</span>
  <span>Widerruf</span>
  <span>Wiederherstellung</span>
</div>

</div>

<div v-click class="criterion-card">

<div class="criterion-number">04</div>

<div class="criterion-icon">
DEV
</div>

<h3>Implementierung</h3>

<div class="criterion-items">
  <span>Backend-Komplexität</span>
  <span>Frontend-Integration</span>
  <span>Credential Storage</span>
  <span>Fehlerbehandlung</span>
</div>

</div>

</div>

<div v-click class="criteria-rule">

<span>PRINZIP</span>

<strong>
Nicht „welches Verfahren gewinnt?“ —
sondern welche Eigenschaften und Trade-offs sind nachweisbar?
</strong>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 18 – METHODIK                                   -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
17 / METHODIK
</div>

# Von der Literatur

# zum Experiment.

<p class="slide-lead">
Literaturbasierte Kriterien werden in einem
<span class="accent">kontrollierten Prototyp praktisch untersucht.</span>
</p>

<div class="method-pipeline">

<div v-click class="method-stage">

<div class="method-number">
01
</div>

<div class="method-symbol">
LIT
</div>

<h3>Literaturrecherche</h3>

<p>
Standards, wissenschaftliche Literatur
und Sicherheitsrichtlinien.
</p>

</div>

<div v-click class="method-connector">
→
</div>

<div v-click class="method-stage">

<div class="method-number">
02
</div>

<div class="method-symbol">
MODEL
</div>

<h3>Kriterienmodell</h3>

<p>
Definition der Sicherheits-,
Usability- und Implementierungskriterien.
</p>

</div>

<div v-click class="method-connector">
→
</div>

<div v-click class="method-stage featured-method">

<div class="method-number">
03
</div>

<div class="method-symbol">
BUILD
</div>

<h3>Prototyp</h3>

<p>
Drei Verfahren unter möglichst
gleichen Rahmenbedingungen.
</p>

</div>

<div v-click class="method-connector">
→
</div>

<div v-click class="method-stage">

<div class="method-number">
04
</div>

<div class="method-symbol">
TEST
</div>

<h3>Evaluation</h3>

<p>
Definierte Szenarien,
Messungen und Beobachtungen.
</p>

</div>

<div v-click class="method-connector">
→
</div>

<div v-click class="method-stage">

<div class="method-number">
05
</div>

<div class="method-symbol">
CMP
</div>

<h3>Vergleich</h3>

<p>
Systematische Gegenüberstellung
der Ergebnisse.
</p>

</div>

</div>

<div v-click class="reproducibility">

<div class="repro-label">
NACHVOLLZIEHBARKEIT
</div>

<div class="repro-items">

<span>
definierte Testfälle
</span>

<span>
gleiche Testumgebung
</span>

<span>
dokumentierte Messgrößen
</span>

<span>
reproduzierbarer Prototyp
</span>

</div>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 19 – PRAKTISCHER TEIL                           -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
18 / PRAKTISCHER TEIL
</div>

# Eine Anwendung.

# Drei Authentifizierungswege.

<p class="slide-lead">
Der Prototyp hält die Anwendung konstant —
<span class="accent">nur die Authentifizierungsstrategie verändert sich.</span>
</p>

<div class="prototype-architecture">

<div v-click class="prototype-client">

<div class="architecture-label">
CLIENT
</div>

<div class="architecture-box angular-box">

<span class="tech-label">
ANGULAR
</span>

<strong>
Web Frontend
</strong>

<small>
Registration · Login · Recovery
</small>

</div>

</div>

<div v-click class="architecture-link">

<div class="api-label">
HTTPS / API
</div>

<div class="api-line">
→
</div>

</div>

<div v-click class="prototype-server">

<div class="architecture-label">
SERVER
</div>

<div class="architecture-box spring-box">

<span class="tech-label">
SPRING BOOT
</span>

<strong>
Authentication Backend
</strong>

<small>
Credential Management · Verification
</small>

</div>

</div>

<div v-click class="architecture-link">

<div class="api-label">
PERSIST
</div>

<div class="api-line">
→
</div>

</div>

<div v-click class="prototype-db">

<div class="architecture-label">
DATA
</div>

<div class="architecture-box database-box">

<span class="tech-label">
DATABASE
</span>

<strong>
Credential Store
</strong>

<small>
User · Public Keys · TOTP Data
</small>

</div>

</div>

</div>

<div class="auth-branches">

<div v-click class="auth-branch">

<span class="branch-id">
A
</span>

<div>
<strong>Password + TOTP</strong>
<small>Shared-secret-basierte MFA</small>
</div>

</div>

<div v-click class="auth-branch">

<span class="branch-id">
B
</span>

<div>
<strong>Synced Passkey</strong>
<small>WebAuthn / Multi-Device Credential</small>
</div>

</div>

<div v-click class="auth-branch">

<span class="branch-id">
C
</span>

<div>
<strong>Security Key</strong>
<small>WebAuthn / Hardware Authenticator</small>
</div>

</div>

</div>

<div v-click class="prototype-principle">

<span>CONTROLLED VARIABLE</span>

Anwendungslogik und Testumgebung bleiben möglichst konstant.
<strong>Authentifizierung ist die Vergleichsvariable.</strong>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 20 – EXPERIMENTDESIGN                           -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
19 / EVALUATION
</div>

# Nicht demonstrieren.

# Messen und vergleichen.

<p class="slide-lead">
Für jedes Verfahren werden dieselben
<span class="accent">definierten Szenarien</span>
durchlaufen.
</p>

<div class="experiment-layout">

<div class="scenario-list">

<div v-click class="scenario">

<span class="scenario-id">
E01
</span>

<div>
<strong>Enrollment</strong>
<p>
Registrierung eines neuen Credentials.
</p>
</div>

<div class="scenario-measure">
STEPS / TIME
</div>

</div>

<div v-click class="scenario">

<span class="scenario-id">
E02
</span>

<div>
<strong>Normal Login</strong>
<p>
Authentifizierung im vorgesehenen Ablauf.
</p>
</div>

<div class="scenario-measure">
STEPS / TIME
</div>

</div>

<div v-click class="scenario">

<span class="scenario-id">
E03
</span>

<div>
<strong>Phishing / Relay</strong>
<p>
Analyse des Verhaltens gegenüber einem falschen Verifier.
</p>
</div>

<div class="scenario-measure">
SECURITY
</div>

</div>

<div v-click class="scenario">

<span class="scenario-id">
E04
</span>

<div>
<strong>Credential Loss</strong>
<p>
Verlust eines Authenticators oder Credentials.
</p>
</div>

<div class="scenario-measure">
RECOVERY
</div>

</div>

<div v-click class="scenario">

<span class="scenario-id">
E05
</span>

<div>
<strong>Credential Revocation</strong>
<p>
Entfernung eines bestehenden Credentials.
</p>
</div>

<div class="scenario-measure">
RECOVERY
</div>

</div>

</div>

<div v-click class="measurement-panel">

<div class="measurement-label">
MEASUREMENT
</div>

<div class="measurement-main">
Messbare Daten
</div>

<div class="measurement-item">
<span>01</span>
Interaktionsschritte
</div>

<div class="measurement-item">
<span>02</span>
Bearbeitungszeit
</div>

<div class="measurement-item">
<span>03</span>
Implementierungsartefakte
</div>

<div class="measurement-item">
<span>04</span>
Sicherheitsverhalten
</div>

<div class="measurement-divider"></div>

<div class="measurement-note">
Gleiche Szenarien.<br>
Gleiche Umgebung.<br>
Unterschiedliche Verfahren.
</div>

</div>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 21 – ERWARTETER ERKENNTNISGEWINN                -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
20 / ERWARTETER ERKENNTNISGEWINN
</div>

# Kein Gewinner.

# Sondern Entscheidungsgrundlagen.

<p class="slide-lead">
Die Arbeit soll sichtbar machen,
<span class="accent">welche Trade-offs die drei Strategien in der Praxis erzeugen.</span>
</p>

<div class="contribution-grid">

<div v-click class="contribution-card">

<span class="contribution-id">01 / TECHNISCH</span>

<div class="contribution-symbol">
BUILD
</div>

<h3>Referenzimplementierung</h3>

<p>
Drei Authentifizierungsstrategien innerhalb
derselben Webanwendung.
</p>

</div>

<div v-click class="contribution-card">

<span class="contribution-id">02 / METHODISCH</span>

<div class="contribution-symbol">
EVAL
</div>

<h3>Vergleichsmodell</h3>

<p>
Einheitliche Kriterien und Szenarien für
Sicherheit, Usability, Recovery und Integration.
</p>

</div>

<div v-click class="contribution-card">

<span class="contribution-id">03 / PRAKTISCH</span>

<div class="contribution-symbol">
DECIDE
</div>

<h3>Entscheidungsgrundlage</h3>

<p>
Nachvollziehbare Trade-offs für Entwickler
und Organisationen.
</p>

</div>

</div>

<div v-click class="contribution-result">

<span>OUTPUT</span>

<strong>
Nicht: „X ist immer besser.“
</strong>

<div class="result-arrow">→</div>

<strong class="accent-result">
„Unter diesen Anforderungen entstehen diese Trade-offs.“
</strong>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 22 – SCOPE & VORGEHEN                           -->
<!-- ===================================================== -->

<div class="content-slide">

<div class="slide-kicker">
21 / ABGRENZUNG & VORGEHEN
</div>

# Klarer Scope.

# Reproduzierbares Vorgehen.

<div class="scope-plan-layout">

<div v-click class="scope-boundary">

<div class="boundary-label">
IM SCOPE
</div>

<div class="boundary-item">
<span>✓</span>
TOTP-basierte Zwei-Faktor-Authentifizierung
</div>

<div class="boundary-item">
<span>✓</span>
Synced Passkeys via WebAuthn
</div>

<div class="boundary-item">
<span>✓</span>
Hardware Security Keys via WebAuthn
</div>

<div class="boundary-item">
<span>✓</span>
Security · Usability · Recovery · Integration
</div>

</div>

<div v-click class="scope-boundary out-boundary">

<div class="boundary-label">
NICHT IM FOKUS
</div>

<div class="boundary-item">
<span>—</span>
Vollständige Identity-Management-Plattform
</div>

<div class="boundary-item">
<span>—</span>
Eigenentwicklung kryptographischer Verfahren
</div>

<div class="boundary-item">
<span>—</span>
Allgemeingültiger „Best Auth Method“-Score
</div>

<div class="boundary-item">
<span>—</span>
Produktionsbetrieb im Unternehmensmaßstab
</div>

</div>

</div>

<div v-click class="work-roadmap">

<div class="roadmap-step">
<span>01</span>
<strong>Research</strong>
<small>Literatur & Standards</small>
</div>

<div class="roadmap-line"></div>

<div class="roadmap-step">
<span>02</span>
<strong>Design</strong>
<small>Kriterien & Architektur</small>
</div>

<div class="roadmap-line"></div>

<div class="roadmap-step">
<span>03</span>
<strong>Build</strong>
<small>Prototyp</small>
</div>

<div class="roadmap-line"></div>

<div class="roadmap-step">
<span>04</span>
<strong>Evaluate</strong>
<small>Tests & Messungen</small>
</div>

<div class="roadmap-line"></div>

<div class="roadmap-step">
<span>05</span>
<strong>Compare</strong>
<small>Auswertung</small>
</div>

</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 23 – SCHLUSS                                    -->
<!-- ===================================================== -->

<div class="closing-slide">

<div class="closing-kicker">
AUTHENTICATION / SECURITY / USABILITY
</div>

<h1>
Mehr Faktoren sind nicht<br>
automatisch die Antwort.
</h1>

<div class="closing-accent"></div>

<p>
Entscheidend ist,
<strong>wie ein Authentifizierungsverfahren auf konkrete Bedrohungen reagiert</strong>
und welche Trade-offs dadurch entstehen.
</p>

<div v-click class="closing-methods">

<span>TOTP</span>
<span>/</span>
<span>PASSKEY</span>
<span>/</span>
<span>SECURITY KEY</span>

</div>

<div v-click class="closing-question">
Fragen?
</div>

</div>

---

<!-- ===================================================== -->
<!-- FOLIE 24 – LITERATUR                                  -->
<!-- ===================================================== -->

<div class="content-slide literature-slide">

<div class="slide-kicker">
LITERATUR & STANDARDS
</div>

# Technische Grundlage.

<p class="slide-lead">
Ausgewählte Quellen, auf denen die technische Einordnung
dieser Präsentation basiert.
</p>

<div class="literature-list">

<div class="literature-entry">
<span>[01]</span>
<div>
<strong>RFC 6238</strong>
<p>
M'Raihi et al. — TOTP: Time-Based One-Time Password Algorithm.
Internet Engineering Task Force.
</p>
</div>
</div>

<div class="literature-entry">
<span>[02]</span>
<div>
<strong>W3C Web Authentication</strong>
<p>
Web Authentication: An API for accessing Public Key Credentials.
World Wide Web Consortium.
</p>
</div>
</div>

<div class="literature-entry">
<span>[03]</span>
<div>
<strong>FIDO Alliance — FIDO2 / Passkeys</strong>
<p>
Technical specifications and documentation on FIDO authentication
and passkey deployment.
</p>
</div>
</div>

<div class="literature-entry">
<span>[04]</span>
<div>
<strong>NIST SP 800-63B</strong>
<p>
Digital Identity Guidelines — Authentication and Authenticator Management.
National Institute of Standards and Technology.
</p>
</div>
</div>

<div class="literature-entry">
<span>[05]</span>
<div>
<strong>Lyastani et al.</strong>
<p>
Is FIDO2 the Kingslayer of User Authentication?
IEEE Symposium on Security and Privacy, 2020.
</p>
</div>
</div>

<div class="literature-entry">
<span>[06]</span>
<div>
<strong>Farke et al.</strong>
<p>
Exploring FIDO2 Security Keys in a Small Company.
USENIX Symposium on Usable Privacy and Security, 2020.
</p>
</div>
</div>

</div>

<div class="literature-note">
Auswahl für die Präsentation · vollständige Literaturrecherche folgt im Rahmen der Bachelorarbeit
</div>

</div>

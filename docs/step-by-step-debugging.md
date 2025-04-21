# ✅ Step-by-Step Debugging Prep (for Midnight Capture)

## 1. Open Chrome DevTools (F12)
Navigate to the TIQ web app and open DevTools (`F12` or `Cmd+Opt+I`).

### Pin these tabs:
- Console
- Network
- Sources
- Application (for token inspection)

---

## 2. Set up Logging Tools
### Console Tab:
- Check **"Preserve log"**

### Network Tab:
- Check **"Preserve log"**
- Apply filter for keywords:
  - `authorize`, `token`, `negotiate`, `signalr`
  - `consults`, `event`, `walkme`

### Optional: Add Timestamp Logging Script
```javascript
const monitorInterval = setInterval(() => {
    const time = new Date().toLocaleString();
    const status = {
        "⏰ Time": time,
        "📦 TokenManager": window.tokenManager?.getTokens?.() || "Unavailable",
        "🔄 HubConnection state": window.hubConnection?.state || "Unavailable",
    };
    console.log("📡 TIQ Midnight Monitor:", status);
}, 60000);

setTimeout(() => {
    clearInterval(monitorInterval);
    console.log("✅ Midnight logging window complete.");
}, 600000);
```

---

## 🔧 Purpose of the Script
This script doesn’t fix errors — it gives you live, timestamped visibility of key internal states. Especially helpful for:
- ✅ Token expiration moments
- ⚠️ OAuth 400s due to stale PKCE params
- ❌ SignalR retry loops
- ⚠️ `appendChild`/DOM null errors
- ⏰ Silent renewals that fail with no UI indication

It makes your **logs traceable** and your **debugging reproducible**.

---

## 3. Watch for Token Expiry (Around Midnight)
- `tokenManager:renewed`
- `token removed` / `token added`
- `400` errors from `/oauth2/v1/authorize`
- `Missing idToken` errors
- `moment.js` warnings (non-RFC format)
- `HubConnection` reconnect or fail logs

---

## 4. Use Sources Panel for Breakpoints
- Locate `main.js` or `auth.js`
- Place breakpoints near:
  - `.renew()`
  - `connection.start()` / `.stop()`

Check:
- Scope tab (for live token object state)
- Call stack (for async call order)

---

## 5. Inspect Application State
Navigate to `Application` tab → Local Storage / Session Storage

Check:
- Are `idToken` or `accessToken` missing or expired?
- Is token rotation happening correctly?
- Any abnormal timestamps?

---

## 6. Save Data for Later
### HAR File:
- Right-click in **Network** tab → *Save all as HAR with content*

### Console Logs:
- Click inside **Console** → Ctrl+A → Copy → Paste into `.txt` or `.log` file

### Lighthouse Report:
- Run Lighthouse **before and after midnight**
- Save as **HTML** or **JSON**

---

## 7. Capture DOM Errors
Watch for runtime messages like:
```bash
Uncaught (in promise) TypeError: Cannot read properties of null (reading 'appendChild')
```
- These often occur during race conditions post-session teardown

---

## 8. Analyze in the Morning
- Group logs by timestamp
- Identify **first point of failure**
- Compare retries, silences, and success attempts
- Note which tokens were missing or which services (SignalR) didn’t reinit

---

> **Note:** All personally identifiable info, session tokens, and org URLs must be scrubbed or replaced when documenting logs for public or team-sharing.

---

_Last updated: April 2025_

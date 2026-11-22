# Home-v4 <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Home v4</title>
  <style>
    :root {
      --bg-app: #f8f9fa;
      --bg-surface: #ffffff;
      --border: #dadce0;
      --text-main: #202124;
      --text-muted: #5f6368;
      --accent: #1a73e8;
      --accent-hover: #1557b0;
      --danger: #d93025;
      --shadow: 0 1px 3px rgba(60, 64, 67, 0.15), 0 1px 2px rgba(60, 64, 67, 0.3);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background-color: var(--bg-app);
      color: var(--text-main);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    header {
      background: var(--bg-surface);
      border-bottom: 1px solid var(--border);
      padding: 12px 18px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      position: sticky;
      top: 0;
      z-index: 10;
    }

    .logo-btn {
      display: flex;
      align-items: center;
      gap: 10px;
      background: none;
      border: none;
      cursor: pointer;
      padding: 6px 10px;
      border-radius: 8px;
      transition: background 0.15s;
    }

    .logo-btn:hover {
      background: #f1f3f4;
    }

    .logo-icon {
      width: 32px;
      height: 32px;
      background: var(--accent);
      border-radius: 6px;
      display: grid;
      place-items: center;
      color: white;
      font-weight: 700;
      font-size: 16px;
    }

    .logo-text {
      font-size: 19px;
      font-weight: 500;
      color: var(--text-main);
      letter-spacing: -0.3px;
    }

    .sync-status {
      font-size: 12px;
      color: var(--text-muted);
    }

    .editor-badge {
      display: none;
      align-items: center;
      gap: 10px;
      background: #e8f0fe;
      color: var(--accent);
      padding: 6px 12px;
      border-radius: 20px;
      font-size: 13px;
      font-weight: 600;
    }

    .editor-badge.active {
      display: flex;
    }

    .exit-editor-btn {
      background: none;
      border: none;
      color: var(--accent);
      text-decoration: underline;
      cursor: pointer;
      font-size: 12px;
      font-weight: 600;
    }

    main {
      max-width: 850px;
      width: 94%;
      margin: 24px auto;
      background: var(--bg-surface);
      border: 1px solid var(--border);
      border-radius: 8px;
      box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05);
      padding: 28px 22px;
      flex: 1;
    }

    @media (min-width: 700px) {
      main {
        margin: 32px auto;
        padding: 44px 52px;
      }
    }

    .doc-title {
      font-size: 26px;
      font-weight: 600;
      margin-bottom: 8px;
      outline: none;
    }

    .doc-subtitle {
      color: var(--text-muted);
      font-size: 15px;
      margin-bottom: 24px;
      outline: none;
    }

    [contenteditable="true"] {
      border-bottom: 1px dashed var(--accent);
      background: #f8fbff;
      padding: 2px 4px;
    }

    .editor-panel {
      display: none;
      background: #f8f9fa;
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 18px;
      margin-bottom: 28px;
    }

    .editor-panel.active {
      display: block;
    }

    .editor-panel h3 {
      font-size: 15px;
      margin-bottom: 12px;
    }

    .form-row {
      display: grid;
      grid-template-columns: 1fr;
      gap: 10px;
    }

    @media (min-width: 680px) {
      .form-row {
        grid-template-columns: 1fr 1.5fr 140px auto;
      }
    }

    input, select {
      padding: 10px 12px;
      border: 1px solid var(--border);
      border-radius: 6px;
      font-size: 15px;
      background: #fff;
      outline: none;
    }

    input:focus, select:focus {
      border-color: var(--accent);
    }

    .btn-primary {
      background: var(--accent);
      color: white;
      border: none;
      padding: 10px 16px;
      border-radius: 6px;
      font-size: 14px;
      font-weight: 500;
      cursor: pointer;
    }

    .btn-primary:hover {
      background: var(--accent-hover);
    }

    .items-section {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .item-card {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      padding: 12px 16px;
      border: 1px solid var(--border);
      border-radius: 8px;
    }

    .item-link {
      color: var(--accent);
      text-decoration: none;
      font-size: 16px;
      font-weight: 500;
      word-break: break-word;
    }

    .item-link:hover {
      text-decoration: underline;
    }

    .item-button {
      display: inline-block;
      background: var(--accent);
      color: white;
      text-decoration: none;
      padding: 10px 18px;
      border-radius: 6px;
      font-size: 14px;
      font-weight: 500;
      word-break: break-word;
    }

    .item-button:hover {
      background: var(--accent-hover);
    }

    .delete-btn {
      display: none;
      background: none;
      border: 1px solid var(--danger);
      color: var(--danger);
      padding: 6px 10px;
      border-radius: 4px;
      font-size: 12px;
      cursor: pointer;
      flex-shrink: 0;
    }

    .delete-btn.active {
      display: inline-block;
    }

    .delete-btn:hover {
      background: #fce8e6;
    }

    .empty-state {
      color: var(--text-muted);
      font-size: 14px;
      text-align: center;
      padding: 32px 12px;
      border: 1px dashed var(--border);
      border-radius: 8px;
    }

    .modal-backdrop {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(32, 33, 36, 0.5);
      place-items: center;
      z-index: 100;
    }

    .modal-backdrop.open {
      display: grid;
    }

    .modal-box {
      background: var(--bg-surface);
      padding: 24px;
      border-radius: 12px;
      width: 90%;
      max-width: 360px;
      box-shadow: var(--shadow);
      text-align: center;
    }

    .modal-box h2 {
      font-size: 18px;
      margin-bottom: 6px;
    }

    .modal-box p {
      font-size: 13px;
      color: var(--text-muted);
      margin-bottom: 16px;
    }

    .modal-box input {
      width: 100%;
      margin-bottom: 12px;
      text-align: center;
    }

    .modal-actions {
      display: flex;
      gap: 8px;
      justify-content: flex-end;
    }

    .btn-secondary {
      background: #f1f3f4;
      color: var(--text-main);
      border: none;
      padding: 10px 14px;
      border-radius: 6px;
      font-size: 14px;
      cursor: pointer;
    }

    .error-msg {
      color: var(--danger);
      font-size: 12px;
      margin-bottom: 10px;
      min-height: 16px;
    }
  </style>
</head>
<body>

  <header>
    <button class="logo-btn" id="logoTrigger" title="Home v4">
      <div class="logo-icon">H4</div>
      <span class="logo-text">Home v4</span>
    </button>

    <span class="sync-status" id="syncStatus">Local only</span>

    <div class="editor-badge" id="editorBadge">
      <span>Editor</span>
      <button class="exit-editor-btn" id="exitEditorBtn">Exit</button>
    </div>
  </header>

  <main>
    <h1 class="doc-title" id="docTitle">Welcome to Home v4</h1>
    <p class="doc-subtitle" id="docSubtitle">Shared links, resources, and quick buttons for the group.</p>

    <section class="editor-panel" id="editorPanel">
      <h3>Add New Element</h3>
      <form class="form-row" id="addItemForm">
        <input type="text" id="itemLabel" placeholder="Label (e.g., Discord)" required />
        <input type="url" id="itemUrl" placeholder="https://..." required />
        <select id="itemType">
          <option value="link">Text Link</option>
          <option value="button">Button</option>
        </select>
        <button type="submit" class="btn-primary">Add</button>
      </form>
    </section>

    <section class="items-section" id="itemsContainer"></section>
  </main>

  <div class="modal-backdrop" id="codeModal">
    <div class="modal-box">
      <h2>Enter code</h2>
      <p>Enter the access code to unlock editing for Home v4.</p>
      <form id="codeForm">
        <input type="password" id="codeInput" placeholder="Enter code..." autocomplete="off" />
        <div class="error-msg" id="codeError"></div>
        <div class="modal-actions">
          <button type="button" class="btn-secondary" id="cancelModalBtn">Cancel</button>
          <button type="submit" class="btn-primary">Unlock</button>
        </div>
      </form>
    </div>
  </div>

  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/13.3.0/firebase-app.js";
    import {
      getFirestore,
      doc,
      setDoc,
      onSnapshot
    } from "https://www.gstatic.com/firebasejs/13.3.0/firebase-firestore.js";

    const PASSCODE = "editor.1";
    const STORAGE_KEY = "home_v4_data";

    // 1. Replace these placeholders with your Firebase web app config from Firebase Console
    const firebaseConfig = {
      apiKey: "YOUR_API_KEY",
      authDomain: "YOUR_PROJECT.firebaseapp.com",
      projectId: "YOUR_PROJECT_ID",
      storageBucket: "YOUR_PROJECT.firebasestorage.app",
      messagingSenderId: "YOUR_SENDER_ID",
      appId: "YOUR_APP_ID"
    };

    const hasFirebaseConfig = !firebaseConfig.apiKey.startsWith("YOUR_");

    const defaultState = {
      title: "Welcome to Home v4",
      subtitle: "Shared links, resources, and quick buttons for the group.",
      items: [
        { id: 1, label: "Google Drive Folder", url: "https://drive.google.com", type: "button" },
        { id: 2, label: "Group Notes & Guidelines", url: "https://docs.google.com", type: "link" }
      ]
    };

    let appState = JSON.parse(localStorage.getItem(STORAGE_KEY)) || defaultState;
    let isEditor = false;
    let docRef = null;

    // DOM Elements
    const logoTrigger = document.getElementById("logoTrigger");
    const syncStatus = document.getElementById("syncStatus");
    const codeModal = document.getElementById("codeModal");
    const codeForm = document.getElementById("codeForm");
    const codeInput = document.getElementById("codeInput");
    const codeError = document.getElementById("codeError");
    const cancelModalBtn = document.getElementById("cancelModalBtn");
    const editorBadge = document.getElementById("editorBadge");
    const exitEditorBtn = document.getElementById("exitEditorBtn");
    const editorPanel = document.getElementById("editorPanel");
    const addItemForm = document.getElementById("addItemForm");
    const itemsContainer = document.getElementById("itemsContainer");
    const docTitle = document.getElementById("docTitle");
    const docSubtitle = document.getElementById("docSubtitle");

    function render() {
      if (document.activeElement !== docTitle) {
        docTitle.innerText = appState.title;
      }
      if (document.activeElement !== docSubtitle) {
        docSubtitle.innerText = appState.subtitle;
      }

      docTitle.contentEditable = isEditor;
      docSubtitle.contentEditable = isEditor;
      editorPanel.classList.toggle("active", isEditor);
      editorBadge.classList.toggle("active", isEditor);
      syncStatus.style.display = isEditor ? "none" : "inline";

      itemsContainer.innerHTML = "";

      if (!appState.items || appState.items.length === 0) {
        itemsContainer.innerHTML = `<div class="empty-state">No links or buttons added yet.</div>`;
        return;
      }

      appState.items.forEach((item) => {
        const card = document.createElement("div");
        card.className = "item-card";

        const actionEl = document.createElement("a");
        actionEl.href = item.url;
        actionEl.target = "_blank";
        actionEl.rel = "noopener noreferrer";
        actionEl.textContent = item.label;
        actionEl.className = item.type === "button" ? "item-button" : "item-link";

        const delBtn = document.createElement("button");
        delBtn.textContent = "Remove";
        delBtn.className = `delete-btn ${isEditor ? "active" : ""}`;
        delBtn.onclick = () => {
          appState.items = appState.items.filter((i) => i.id !== item.id);
          saveState();
          render();
        };

        card.appendChild(actionEl);
        card.appendChild(delBtn);
        itemsContainer.appendChild(card);
      });
    }

    async function saveState() {
      appState.title = docTitle.innerText.trim() || "Welcome to Home v4";
      appState.subtitle = docSubtitle.innerText.trim() || "";
      localStorage.setItem(STORAGE_KEY, JSON.stringify(appState));

      if (docRef) {
        syncStatus.textContent = "Saving...";
        try {
          await setDoc(docRef, appState);
          syncStatus.textContent = "Synced live";
        } catch (err) {
          syncStatus.textContent = "Sync error";
          console.error(err);
        }
      }
    }

    if (hasFirebaseConfig) {
      const app = initializeApp(firebaseConfig);
      const db = getFirestore(app);
      docRef = doc(db, "home_v4", "main_page");
      syncStatus.textContent = "Connecting...";

      onSnapshot(
        docRef,
        (snapshot) => {
          if (snapshot.exists()) {
            appState = { ...defaultState, ...snapshot.data() };
            localStorage.setItem(STORAGE_KEY, JSON.stringify(appState));
            render();
            syncStatus.textContent = "Synced live";
          } else {
            setDoc(docRef, appState);
          }
        },
        (err) => {
          syncStatus.textContent = "Offline / Rules check";
          console.error(err);
        }
      );
    }

    logoTrigger.addEventListener("click", () => {
      if (isEditor) return;
      codeError.textContent = "";
      codeInput.value = "";
      codeModal.classList.add("open");
      codeInput.focus();
    });

    cancelModalBtn.addEventListener("click", () => {
      codeModal.classList.remove("open");
    });

    codeForm.addEventListener("submit", (e) => {
      e.preventDefault();
      if (codeInput.value.trim() === PASSCODE) {
        isEditor = true;
        codeModal.classList.remove("open");
        render();
      } else {
        codeError.textContent = "Incorrect code. Try again.";
        codeInput.select();
      }
    });

    exitEditorBtn.addEventListener("click", () => {
      saveState();
      isEditor = false;
      render();
    });

    docTitle.addEventListener("blur", saveState);
    docSubtitle.addEventListener("blur", saveState);

    addItemForm.addEventListener("submit", (e) => {
      e.preventDefault();
      const label = document.getElementById("itemLabel").value.trim();
      const url = document.getElementById("itemUrl").value.trim();
      const type = document.getElementById("itemType").value;

      if (!label || !url) return;

      appState.items.push({
        id: Date.now(),
        label,
        url,
        type
      });

      addItemForm.reset();
      saveState();
      render();
    });

    render();
  </script>
</body>
</html>

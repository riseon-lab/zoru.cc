This plan focuses on building a **zero-infrastructure, 1-on-1 video utility**. Since you aren't hosting video data, your "server" is just a delivery mechanism for a single HTML file.

---

## Phase 1: The Core Tech Stack

To keep this free and account-less, use these specific tools:

* **Language:** Vanilla JavaScript (no frameworks to bloat the load time).
* **Engine:** [PeerJS](https://peerjs.com/) (Simplifies WebRTC signaling so you don't have to write 500 lines of handshake code).
* **Hosting:** [GitHub Pages](https://pages.github.com/)

---

## Phase 2: Development (The "One-File" Build)

Create a single `index.html` file. It must handle three logic flows:

### 1. The ID Generator

* When the page loads, check the URL for a hash (e.g., `yoursite.com/#12345`).
* If no hash exists, generate a random 6-character string and update the URL.
* This string is the "Room ID."

### 2. The Media Capture

* Request `navigator.mediaDevices.getUserMedia({ video: true, audio: true })`.
* Immediately display the local stream in a small `<video>` element.

### 3. The Peer Handshake

* **The Caller:** If a user creates the link, they wait for a connection.
* **The Joiner:** If a user opens a link with a hash, they automatically attempt to "call" the ID in that hash.
* **The Connection:** Once the P2P bridge is built, the remote video stream is attached to a main `<video>` element.

---

## Phase 3: The "Senior Peer" UI/UX

To differentiate from Zoom, remove all traditional "app" elements:

* **Zero Buttons:** No "Join" button. Camera starts on page load.
* **Auto-Copy:** As soon as the link is generated, copy it to the user's clipboard automatically or provide a massive "Share Link" button.
* **Responsive Grid:** Only two states: 100% height (self-view) or 50/50 split (when the peer joins).
* **The "Burner" Feature:** Add a script that closes the connection if the tab is inactive for more than 2 minutes.

---

## Phase 4: Deployment & Optimization

1. **Push to GitHub:** Create a repository and enable "Pages" in settings. Your site is now live at `username.github.io/project`.
2. **Add STUN Servers:** In your PeerJS config, add Google's public STUN list:
```javascript
{
  config: { 'iceServers': [{ 'urls': 'stun:stun.l.google.com:19302' }] }
}

```


3. **Bitrate Cap:** Force the video resolution to 720p maximum. This ensures the P2P connection stays stable even on mediocre mobile data.

---

## Action Items Comparison

| Task | Estimated Time | Complexity |
| --- | --- | --- |
| Basic WebRTC Handshake | 2 Hours | Medium |
| URL/Hash Logic | 30 Mins | Low |
| Mobile-First CSS | 1 Hour | Low |
| GitHub Pages Deployment | 15 Mins | Low |

---


domain name = zoru.cc 


The Branding
Tagline: Direct. Private. Temporary.

UI Style: Dark mode, high-contrast monospace fonts (e.g., Courier or Roboto Mono), and zero unnecessary buttons.


the UI can feel really premium but completey minimal. we want it to just work. 
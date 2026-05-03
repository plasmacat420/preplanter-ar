# Troubleshooting Guide

Having issues with PrePlanter AR? Here are common problems and solutions.

## 🔍 General Issues

### AR Experience Won't Load
**Problem:** Page shows "loading..." but never starts

**Solutions:**
1. **Check browser compatibility**
   - Chrome/Chromium recommended
   - Safari has limited WebGL support
   - Firefox should work, but test in Chrome first

2. **Check browser console for errors**
   - Press `F12` to open DevTools
   - Look for red error messages in Console tab
   - Share errors in a GitHub issue

3. **Clear cache and reload**
   ```bash
   Ctrl+Shift+Delete (or Cmd+Shift+Delete on Mac)
   ```
   Select "All time" and clear cached images/files

4. **Try a different browser**
   - Test in Chrome, Edge, Firefox
   - Eliminates browser-specific issues

---

## 📷 Camera & Permission Issues

### Camera Permission Denied
**Problem:** Browser shows "Camera blocked" or asks for permission repeatedly

**Solutions:**
1. **Reset browser permissions**
   - Chrome: Settings → Privacy → Site settings → Camera
   - Firefox: Preferences → Privacy → Permissions → Camera
   - Allow `plasmacat420.github.io/preplanter-ar`

2. **Check OS camera permissions**
   - Windows: Settings → Privacy & Security → Camera
   - macOS: System Preferences → Security & Privacy → Camera
   - Allow your browser access

3. **Restart browser**
   - Close all tabs and reopen
   - Sometimes permissions cache incorrectly

---

## 🎯 AR Tracking Issues

### Logo Not Recognized / "Scanning" Stays Forever
**Problem:** Pointing at logo doesn't trigger plant animation

**Solutions:**
1. **Good lighting is essential**
   - ✅ Bright, even lighting
   - ❌ Avoid shadows or backlight
   - Use natural daylight if possible
   - Avoid harsh glare

2. **Hold logo steady and visible**
   - Keep the entire logo in frame
   - Hold camera ~6-12 inches away
   - Avoid moving too quickly
   - Wait 1-2 seconds for tracking to lock

3. **Use the original logo**
   - The app is trained on the PrePlanter logo
   - Degraded/printed logos may not work
   - Try a digital screen version
   - Higher resolution = better tracking

4. **Check targets.mind file**
   - Verify `targets.mind` exists in repo root
   - File size should be ~334KB
   - If corrupted, recompile using `compile.html`

5. **Lower device angle**
   - AR works best when logo is 20-60° to camera
   - Too perpendicular = harder to track

---

## 🖥️ Local Development Issues

### "Cannot GET /" Error
**Problem:** `npm run dev` fails or shows 404

**Solutions:**
1. **Verify you're in the right directory**
   ```bash
   pwd  # Should show preplanter-ar folder
   ls   # Should see index.html, compile.html, etc
   ```

2. **Kill existing server on port 3000**
   ```bash
   # On Windows (PowerShell)
   netstat -ano | findstr :3000
   taskkill /PID <PID> /F
   
   # On Mac/Linux
   lsof -ti:3000 | xargs kill -9
   ```

3. **Try different port**
   ```bash
   npx serve --port 3001
   ```

4. **Reinstall dependencies**
   ```bash
   rm -rf node_modules package-lock.json
   npm install
   npm run dev
   ```

---

## 📦 AR Target Compilation Issues

### Compile.html Won't Load
**Problem:** `compile.html` shows error or blank page

**Solutions:**
1. **Verify MindAR library loads**
   - Open DevTools Console (F12)
   - Look for CORS or network errors
   - Check internet connection

2. **Use Chrome browser**
   - MindAR works best in Chrome
   - Firefox may have import issues

3. **Allow pop-ups**
   - Some browsers block file downloads
   - Check browser pop-up settings

### Compilation Fails / Stuck at "Compiling..."
**Problem:** Progress bar doesn't move or shows error

**Solutions:**
1. **Use a high-quality PNG image**
   - Minimum: 512×512 px
   - RGB color space (not CMYK)
   - Clear, high-contrast designs work best

2. **Try a different image**
   - Test with the original `logo.png`
   - Verify image loads by checking preview

3. **Clear browser cache**
   - DevTools → Application → Clear storage
   - Reload page and try again

4. **Use Chrome (not Firefox)**
   - Firefox import/export may timeout
   - Chrome is more stable

---

## ⚡ Performance Issues

### Animation is Choppy / Laggy
**Problem:** Plant animation stutters or FPS drops

**Solutions:**
1. **Close other browser tabs**
   - Free up system resources
   - AR is GPU-intensive

2. **Check device specs**
   - Low-end phones may struggle
   - Close background apps
   - Restart device if needed

3. **Reduce animation quality (temporary)**
   - Open DevTools Console
   - Paste: `renderer.setPixelRatio(1)`
   - Reload page

4. **Check device temperature**
   - Extended AR sessions heat up devices
   - Take breaks to cool down

### High Battery Drain
**Problem:** Battery depletes quickly during AR session

**Solutions:**
1. **This is normal for AR**
   - Camera + GPU = high power usage
   - Similar to video calls or games

2. **Mitigation strategies**
   - Reduce screen brightness
   - Close other apps
   - Use lower pixel ratio
   - Limit session duration

---

## 🌍 Accessibility Issues

### Text Too Small / Hard to Read
**Problem:** Can't read scan instructions

**Solutions:**
1. **Browser zoom**
   - Chrome: Ctrl/Cmd + `+` to zoom in
   - Reload after zooming

2. **Accessibility settings**
   - OS: Enable larger fonts
   - Browser: Adjust font sizes

### Touch Controls Not Working
**Problem:** Can't tap buttons on mobile

**Solutions:**
1. **Full-screen mode**
   - Some AR apps need fullscreen
   - Try Chrome on Android with fullscreen

2. **Tap in center of button**
   - Buttons are small on mobile
   - Tap precisely on the text

---

## 🔗 Network / Online Issues

### Loads Locally but Not on GitHub Pages
**Problem:** Works on `localhost:3000` but not `github.io`

**Solutions:**
1. **Check GitHub Pages is enabled**
   - Repo Settings → Pages
   - Source should be "main branch" or "deploy" branch
   - Wait 1-2 minutes for deployment

2. **Clear browser cache**
   - GitHub Pages has delays
   - Hard refresh: Ctrl+Shift+R (or Cmd+Shift+R)

3. **Check HTTPS enabled**
   - GitHub Pages requires HTTPS
   - Your live URL should be `https://plasmacat420.github.io/preplanter-ar/`

---

## 🆘 Still Having Issues?

### Before Opening an Issue
1. ✅ Check this troubleshooting guide
2. ✅ Test in Chrome browser
3. ✅ Clear cache and retry
4. ✅ Check browser console for errors (F12)

### Opening a GitHub Issue
Please include:
- **Browser & OS**: Chrome on Windows 10, etc.
- **What you did**: Steps to reproduce
- **What happened**: Error message or unexpected behavior
- **Screenshots/Console errors**: Paste any error text
- **Device type**: Desktop, phone, tablet

**Good issue example:**
```
Title: AR tracking fails with printed logo on mobile

Device: iPhone 12 running iOS 16
Browser: Safari 16
Steps:
1. Open live demo
2. Point at printed PrePlanter logo
3. Wait 10+ seconds
4. No plant animation appears

Expected: Plant grows when logo is scanned
Actual: "scanning..." text stays on screen

Console error: [paste any errors here]
```

---

## 📚 More Resources

- **Main docs:** [README.md](README.md)
- **Contributing:** [CONTRIBUTING.md](CONTRIBUTING.md)
- **MindAR docs:** https://mind-ar.github.io/
- **Three.js docs:** https://threejs.org/docs/

---

**Can't find your issue?** Open a GitHub Discussion or tag @plasmacat420! 🌱

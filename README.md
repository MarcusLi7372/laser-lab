# Laser Lab

Website for **Laser Lab**, a custom 3D printing shop.

Customers swipe through 3D prints, tap one to watch a 3D printer build it, answer a few quick questions (who it's for, color, a name to laser-engrave onto the print), then pick a color and drag a slider to choose the size before ordering.

## What's in this folder

| File | What it is |
| --- | --- |
| `index.html` | The whole website (HTML, CSS and JavaScript in one file) |
| `assets/logo.webp` | The Laser Lab logo with a see-through background |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |

The 3D graphics use [three.js](https://threejs.org) r128, loaded from a CDN, so there is nothing to install or build.

## Put it online with GitHub Pages

1. Create a new repository on GitHub (for example `laser-lab`).
2. Upload everything in this folder (keep the `assets` folder).
3. In the repository, go to **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then **Save**.
5. After a minute the site is live at `https://<your-username>.github.io/laser-lab/`.

To use your own domain (like `laserlab.ca`), add it under **Settings → Pages → Custom domain**.

## Try it on your computer

Open `index.html` in a browser, or run a small local server from this folder:

```bash
python3 -m http.server 8000
```

Then go to http://localhost:8000.

## Things to update before launch

- **Products and prices** are samples. Edit the `PRODUCTS` list near the top of the `<script>` in `index.html` (name, base price, height in cm, layers, print time, fun fact).
- **Colors** are in the `COLORS` list right below it. Size runs from 80% to 130% of each product's height, and the price scales from 0.8x to 1.5x the base price (see `curSize()`).
- **Payments** use PayPal checkout (PayPal or debit/credit card, in CAD, pickup only, no shipping). The PayPal Client ID is the `PAYPAL_CLIENT_ID` line in `index.html`. Use a **Sandbox** Client ID for testing and swap in the **Live** Client ID from the account owner (a parent) to take real money. Only the Client ID goes in the site, never the Secret. If PayPal can't load, the page falls back to a simple order request form.
- **After someone pays,** PayPal emails the account owner. The buyer's name and contact are in the payment's custom ID, and the color, size and engraved name are in the item description. Check that the amount paid matches the order before printing.
- **Reviews** on GitHub Pages are saved only in the visitor's own browser session. Sharing reviews between all visitors needs a small backend (for example Firebase or Supabase).

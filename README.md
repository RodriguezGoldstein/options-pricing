# Monte Carlo Option Pricing Simulation

This repository also includes a self-contained HTML demo `index.html` that demonstrates Monte Carlo pricing of European options (call/put) with a few variance reduction techniques and interactive visualizations powered by D3.

Key features:
- Monte Carlo simulation of asset price paths under geometric Brownian motion.
- Antithetic variates and an optional control variate (based on discounted terminal asset) to reduce estimator variance.
- Histogram of discounted payoff, estimator comparison (MC, MC+CV, Black–Scholes), sample price paths, and payoff scatter at expiry.
- Interactive zoom/pan on charts; per-chart clipping preserves axes while plotting is clipped to the viewport.
- Uses a Blob-based Web Worker to run heavy simulations off the main thread (keeps the UI responsive). The app falls back to main-thread simulation when Workers are unavailable.

How to run the example locally:

1. Serve the project over HTTP (do not open the file via `file://`):

   ```bash
   # Python 3
   python3 -m http.server 8000

   # or via a simple npm server
   npx http-server -p 8000
   ```

2. Open `http://localhost:8000/index.html` in a modern browser.

Deploying to GitHub Pages:

- The demo is self-contained and works on GH Pages. The Blob-based Web Worker is created in-browser, so no server-side changes are required. Push the repository or the single HTML file to a branch configured for GitHub Pages and open the page via the GH Pages URL.
- Note: if you plan to import external scripts inside the worker, ensure they are same-origin or CORS-enabled.

Quick usage notes:
- Controls are at the top of the page (S₀, K, r, σ, T, steps, paths, seed, antithetic, control variate).
- Click **Run Simulation** to compute results and re-render all charts.

## Development workflow

- **Install dependencies**: `npm install`
- **Lint JavaScript**: `npm run lint`
- **Check formatting**: `npm run format:check`
- **Apply formatting**: `npm run format`
- **Serve locally**: `npm start` (launches HTTP server on port 8080)

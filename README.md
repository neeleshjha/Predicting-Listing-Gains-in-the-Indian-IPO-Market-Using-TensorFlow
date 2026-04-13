<header class="hero">
  <div class="hero-inner">
    <div class="badge"><span>📓</span> Deep Learning · TensorFlow · Keras</div>
    <h1>IPO Listing Profit<br>Predictor</h1>
    <p class="hero-sub">
      A deep learning classification model that predicts whether an Indian IPO will
      list at a profit on its first trading day — built with TensorFlow and Keras on
      real market data.
    </p>
    <div class="tag-row">
      <span class="tag">Python</span>
      <span class="tag">TensorFlow 2.x</span>
      <span class="tag">Keras Sequential API</span>
      <span class="tag">Pandas</span>
      <span class="tag">Scikit-learn</span>
      <span class="tag">Seaborn</span>
    </div>
  </div>
</header>

<main>

  <!-- ABOUT -->
  <section>
    <h2>
      <span class="icon" style="background:rgba(59,130,246,0.15);">📌</span>
      About This Project
    </h2>
    <p>
      When a company goes public through an IPO (Initial Public Offering), investors
      want to know: <em>will the stock price rise or fall on day one?</em> This project
      tackles exactly that question using a neural network trained on 319 real IPO
      listings from the Indian stock market.
    </p>
    <p>
      The model takes in key subscription and pricing data for an IPO and outputs a
      binary prediction — <strong>profit (1)</strong> or <strong>no profit (0)</strong> —
      achieving ~74% accuracy on unseen data.
    </p>
  </section>

  <!-- DATASET -->
  <section>
    <h2>
      <span class="icon" style="background:rgba(34,211,238,0.12);">🗄️</span>
      The Dataset
    </h2>
    <p>
      The dataset (<code>Indian_IPO_Market_Data.csv</code>) contains <strong>319 IPO
      records</strong> with 9 columns. After cleaning, 6 features are used to train
      the model:
    </p>
    <br/>
    <div class="card" style="padding:0; overflow:hidden;">
      <table>
        <thead>
          <tr>
            <th>Column</th>
            <th>Description</th>
            <th>Type</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Issue_Size</td><td>Total size of the IPO offering</td><td><span class="pill blue">Feature</span></td></tr>
          <tr><td>Subscription_QIB</td><td>Subscription by Qualified Institutional Buyers</td><td><span class="pill blue">Feature</span></td></tr>
          <tr><td>Subscription_HNI</td><td>Subscription by High Net-worth Individuals</td><td><span class="pill blue">Feature</span></td></tr>
          <tr><td>Subscription_RII</td><td>Subscription by Retail Individual Investors</td><td><span class="pill blue">Feature</span></td></tr>
          <tr><td>Subscription_Total</td><td>Total overall subscription rate</td><td><span class="pill blue">Feature</span></td></tr>
          <tr><td>Issue_Price</td><td>Price at which shares were offered</td><td><span class="pill blue">Feature</span></td></tr>
          <tr><td>Listing_Gains_Profit</td><td>Did the IPO list at a profit? (1=Yes, 0=No)</td><td><span class="pill green">Target</span></td></tr>
        </tbody>
      </table>
    </div>
  </section>

  <!-- PIPELINE -->
  <section>
    <h2>
      <span class="icon" style="background:rgba(167,139,250,0.12);">⚙️</span>
      How It Works — Step by Step
    </h2>
    <div class="pipeline">
      <div class="step" data-n="1">
        <div class="step-body">
          <div class="step-title">Load & Explore Data</div>
          <p>The CSV is loaded with Pandas. Basic stats are examined and the target
          variable (<code>Listing_Gains_Profit</code>) is created from the raw gains
          percentage column. ~55% of IPOs listed at a profit, making the dataset
          fairly balanced.</p>
        </div>
      </div>
      <div class="step" data-n="2">
        <div class="step-body">
          <div class="step-title">Data Visualization</div>
          <p>Histograms, boxplots, and scatter plots are used to understand distributions
          and spot outliers. Key finding: IPOs that listed at a loss had significantly
          more extreme price outliers.</p>
        </div>
      </div>
      <div class="step" data-n="3">
        <div class="step-body">
          <div class="step-title">Outlier Treatment</div>
          <p>The IQR (Interquartile Range) method is applied to each feature. Values
          beyond 1.5× IQR are clipped to the upper/lower bounds, preventing extreme
          values from skewing the model.</p>
        </div>
      </div>
      <div class="step" data-n="4">
        <div class="step-body">
          <div class="step-title">Normalization</div>
          <p>All 6 predictor variables are scaled to a 0–1 range by dividing by their
          maximum value. This ensures no single feature dominates training due to
          its scale.</p>
        </div>
      </div>
      <div class="step" data-n="5">
        <div class="step-body">
          <div class="step-title">Train / Test Split</div>
          <p>The dataset is split 70/30 — 223 samples for training, 96 for testing —
          using a fixed random seed for reproducibility.</p>
        </div>
      </div>
      <div class="step" data-n="6">
        <div class="step-body">
          <div class="step-title">Build the Neural Network</div>
          <p>A Sequential model is built in Keras with 4 hidden layers using ReLU
          activations, and a final sigmoid output layer for binary classification.</p>
        </div>
      </div>
      <div class="step" data-n="7">
        <div class="step-body">
          <div class="step-title">Train & Evaluate</div>
          <p>The model is compiled with the Adam optimizer and Binary Crossentropy
          loss, then trained for 250 epochs. Accuracy improves steadily over training.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ARCHITECTURE -->
  <section>
    <h2>
      <span class="icon" style="background:rgba(251,191,36,0.12);">🧠</span>
      Neural Network Architecture
    </h2>
    <div class="arch-grid">
      <div class="arch-row">
        <span class="arch-layer">Input Layer</span>
        <span class="arch-meta">6 features</span>
      </div>
      <div class="arch-arrow">↓</div>
      <div class="arch-row">
        <span class="arch-layer">Dense Layer 1</span>
        <span class="arch-meta">32 neurons · ReLU · 224 params</span>
      </div>
      <div class="arch-arrow">↓</div>
      <div class="arch-row">
        <span class="arch-layer">Dense Layer 2</span>
        <span class="arch-meta">16 neurons · ReLU · 528 params</span>
      </div>
      <div class="arch-arrow">↓</div>
      <div class="arch-row">
        <span class="arch-layer">Dense Layer 3</span>
        <span class="arch-meta">8 neurons · ReLU</span>
      </div>
      <div class="arch-arrow">↓</div>
      <div class="arch-row">
        <span class="arch-layer">Dense Layer 4</span>
        <span class="arch-meta">4 neurons · ReLU</span>
      </div>
      <div class="arch-arrow">↓</div>
      <div class="arch-row output">
        <span class="arch-layer" style="color:#67e8f9;">Output Layer</span>
        <span class="arch-meta">1 neuron · Sigmoid · Binary output</span>
      </div>
    </div>
    <br/>
    <p style="font-size:0.88rem;">
      <strong style="color:#e2e8f0;">Optimizer:</strong> Adam (lr = 0.001) &nbsp;·&nbsp;
      <strong style="color:#e2e8f0;">Loss:</strong> Binary Crossentropy &nbsp;·&nbsp;
      <strong style="color:#e2e8f0;">Epochs:</strong> 250
    </p>
  </section>

  <!-- RESULTS -->
  <section>
    <h2>
      <span class="icon" style="background:rgba(52,211,153,0.12);">📊</span>
      Results
    </h2>
    <div class="metrics">
      <div class="metric-card highlight">
        <div class="metric-value">74.9%</div>
        <div class="metric-label">Training Accuracy</div>
      </div>
      <div class="metric-card highlight">
        <div class="metric-value">73.9%</div>
        <div class="metric-label">Test Accuracy</div>
      </div>
    </div>
    <br/>
    <p>
      The small gap between training and test accuracy (~1%) is a positive sign —
      it means the model is <strong style="color:#e2e8f0;">not overfitting</strong>.
      It generalises well to new IPO data it has never seen before.
    </p>
  </section>

  <!-- FEATURES -->
  <section>
    <h2>
      <span class="icon" style="background:rgba(59,130,246,0.12);">✨</span>
      Key Features
    </h2>
    <div class="feat-grid">
      <div class="feat-card">
        <div class="feat-icon">📈</div>
        <div class="feat-title">Real IPO Market Data</div>
        <div class="feat-desc">Trained on 319 actual IPO listings from the Indian stock market — not synthetic data.</div>
      </div>
      <div class="feat-card">
        <div class="feat-icon">🔍</div>
        <div class="feat-title">Exploratory Analysis</div>
        <div class="feat-desc">Thorough EDA with distributions, boxplots, and correlation scatter plots before modelling.</div>
      </div>
      <div class="feat-card">
        <div class="feat-icon">🧹</div>
        <div class="feat-title">Outlier Handling</div>
        <div class="feat-desc">IQR-based clipping ensures extreme values don't distort the neural network's learning.</div>
      </div>
      <div class="feat-card">
        <div class="feat-icon">⚖️</div>
        <div class="feat-title">Balanced Dataset</div>
        <div class="feat-desc">~55% profit vs 45% no-profit split means the model isn't biased toward one class.</div>
      </div>
      <div class="feat-card">
        <div class="feat-icon">🏗️</div>
        <div class="feat-title">4-Layer Deep Network</div>
        <div class="feat-desc">Sequential Keras model with progressively smaller layers (32→16→8→4→1) for efficient classification.</div>
      </div>
      <div class="feat-card">
        <div class="feat-icon">🔁</div>
        <div class="feat-title">Reproducible Results</div>
        <div class="feat-desc">Fixed random seeds on both TensorFlow and Scikit-learn ensure consistent outputs on every run.</div>
      </div>
    </div>
  </section>

  <!-- CONCLUSION -->
  <section>
    <h2>
      <span class="icon" style="background:rgba(167,139,250,0.12);">🏁</span>
      Conclusion
    </h2>
    <div class="conclusion">
      <p>
        This project demonstrates how deep learning can be applied to financial market
        prediction. Starting from raw IPO data, the notebook walks through every stage —
        exploration, cleaning, visualisation, feature engineering, modelling, and
        evaluation — in a clear and reproducible way.
      </p>
      <br/>
      <p>
        The final model achieves a consistent <strong style="color:#6ee7b7;">~74% accuracy</strong>
        on both training and test sets, confirming it has learned genuine patterns
        rather than memorised the training data. This is a solid baseline; further
        improvements could come from hyperparameter tuning, dropout regularisation,
        additional features, or trying other architectures.
      </p>
    </div>
  </section>

</main>

<footer>
  Built with TensorFlow · Keras · Pandas · Seaborn &nbsp;|&nbsp; Indian IPO Market Dataset · 319 records
</footer>

</body>
</html>

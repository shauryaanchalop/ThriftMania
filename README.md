<div align="center">
  <img src="logo.png" alt="ThriftMania Logo" width="100" height="auto" />
  <h1>ThriftMania | Digital Archive</h1>
  <p>
    <strong>A Brutalist E-Commerce Experience for Vintage Streetwear</strong>
  </p>
  
  <p>
    <a href="https://thriftmania.netlify.app/" target="_blank">View Live Demo</a>
  </p>

  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" />
  <img src="https://img.shields.io/badge/Design-Brutalist-black?style=for-the-badge" />
</div>

<br />

## 📂 Project Overview

**ThriftMania** is not just an online store; it is a digital archive for curated vintage clothing. The project bridges the gap between retro fashion culture and modern web design. 

Built with a **"High-Impact, Low-Friction"** philosophy, the site features a custom brutalist aesthetic, seamless interactions, and a direct-to-WhatsApp checkout flow tailored for the Indian thrift market.


## ✨ Key Features

### 🎨 UI/UX Design
- **Cinematic Entrance:** Text reveal animations and smooth hero section fade-ins.
- **Custom Cursor:** Interactive custom cursor with hover-state scaling (Desktop only).
- **Aesthetic Overlays:** CSS-based grain/noise overlay and vignette for a vintage film look.
- **Glassmorphism:** Frosted glass navigation utilizing `backdrop-blur`.

### ⚙️ Technical Functionality
- **Persistent Cart:** Uses `localStorage` to save user's cart data across page reloads.
- **Dynamic Filtering:** Category-based filtering (Outerwear, Tees, Denim) without page refreshes.
- **Toast Notifications:** Custom non-blocking popups when items are added to the cart.
- **Sold Out Logic:** Visual handling of out-of-stock items (grayscale + disabled buttons).
- **WhatsApp Checkout:** innovative logic that parses the cart object into a formatted string and opens a pre-filled WhatsApp message to the business owner.

## 🛠 Tech Stack

* **Frontend:** HTML5, Semantic Markup
* **Styling:** Tailwind CSS (via CDN for rapid prototyping), Custom CSS animations
* **Scripting:** Vanilla JavaScript (ES6+)
* **Icons:** Lucide Icons
* **Fonts:** Space Grotesk (Sans) & Playfair Display (Serif)

## 💻 Code Highlight: WhatsApp Checkout Logic

The core feature that removes the need for a complex backend is the direct checkout system:

```javascript
function checkoutToWhatsapp() {
    if (!cart.length) return;
    
    // 1. Build the message header
    let msg = "Hi ThriftMania, I'd like to secure the following from the Archive:\n\n";
    
    // 2. Iterate through cart items
    cart.forEach(i => {
        msg += `• ${i.name} (x${i.qty}) - ₹${(i.price*i.qty).toLocaleString('en-IN')}\n`
    });
    
    // 3. Add Total
    msg += `\n*Total Value: ₹${cart.reduce((a,b)=>a+(b.price*b.qty),0).toLocaleString('en-IN')}*`;
    
    // 4. Open WhatsApp API
    window.open(`https://wa.me/917015603762?text=${encodeURIComponent(msg)}`, '_blank');
}

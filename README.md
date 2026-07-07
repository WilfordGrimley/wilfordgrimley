# HOW-TO

1. **Create a decklist**. My personal recommendation is [Moxfield](https://moxfield.com/) with the [tagger addon](https://github.com/natefinch/moxtags/tree/main), another popular option is [Archidekt](https://archidekt.com/).
2. **Go to [Proxxied](https://proxxied.com/)** proxy builder.
3.  **VERY IMPORTANT Select MPC Autofill**
    <details>
      <summary>
        on the left side of the page under 'Preferred Art Source'.
      </summary>
      <img src="assets/images/preferred-art-source.png" alt="Preferred Art Source Selection MPC Fill" width="50%"/>
    </details>
4. **Import your cards.** Be aware that if you import via url it will include your maybe and sideboards which takes up a lot of memory while editing.  
  -You can check 'auto import tokens' before importing.  
  -You can export just your mainboard and commander from the deckbuilding sites; copy-paste.  
5. **Select art!** Click on each card and find the art you like the best from the ones available on **MPCautofill**. There are sort options available, and you can set specific tags and proxy artist sources as favorites to make importing future decks much quicker.
If the art you want is not available, custom cards can be created using [CardConjurer](https://cardconjurer.app/), and art upscaled with [Upscayl](https://upscayl.org/). You can also select Scryfall as a source if needed.  
6. **Select a cardback.** Flip one of the cards, select a cardback and override the default. Be careful of mdfc.  
7. **Export MPC art selection.**
    <details>
      <summary>On the right side of the page under 'Export', select 'Copy Decklist - With MPC Art IDs'.</summary>
      <img src="assets/images/Copy-Decklist.png" alt="Copy Decklist Button" width="50%"/>
    </details>
    **It is important you copy the MPC Art ID and not the basic decklist.**
    <details>
      <summary>
        Alternatively make an account on Proxxied and create a share link from the top right of the page.
      </summary>
      <img src="assets/images/sharelink.png" alt="Share Link Button" width="50%"/>
    </details>
  
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contact Us</title>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            background-color: #f5f5f5;
        }
        .contact-container {
            background: white;
            padding: 40px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        h1 {
            color: #333;
            margin-bottom: 10px;
        }
        .subtitle {
            color: #666;
            margin-bottom: 30px;
        }
        .form-group {
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            color: #333;
            font-weight: 500;
        }
        input[type="text"],
        input[type="email"],
        textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 14px;
            box-sizing: border-box;
            transition: border-color 0.3s;
        }
        input:focus,
        textarea:focus {
            outline: none;
            border-color: #4A90E2;
        }
        textarea {
            resize: vertical;
            min-height: 120px;
        }
        button {
            background-color: #4A90E2;
            color: white;
            padding: 12px 30px;
            border: none;
            border-radius: 4px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #357ABD;
        }
        button:disabled {
            background-color: #ccc;
            cursor: not-allowed;
        }
        .alert {
            padding: 15px;
            border-radius: 4px;
            margin-bottom: 20px;
            display: none;
        }
        .alert.show {
            display: block;
        }
        .alert-success {
            background-color: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        .alert-error {
            background-color: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }
    </style>
</head>
<body>
    <div class="contact-container">
        <h1>Get in Touch</h1>
        <p class="subtitle">We'd love to hear from you. Send us a message and we'll respond as soon as possible.</p>

        <div id="alertBox" class="alert"></div>

        <form id="contactForm" action="https://api.staticforms.dev/submit" method="POST">
            <div class="form-group">
                <label for="name">Your Name *</label>
                <input type="text" id="name" name="name" required>
            </div>

            <div class="form-group">
                <label for="email">Your Email *</label>
                <input type="email" id="email" name="email" required>
            </div>

            <div class="form-group">
                <label for="subject">Subject</label>
                <input type="text" id="subject" name="subject" placeholder="What's this about?">
            </div>

            <div class="form-group">
                <label for="message">Message *</label>
                <textarea id="message" name="message" required placeholder="Tell us what's on your mind..."></textarea>
            </div>

            <!-- Static Forms Configuration -->
            <input type="hidden" name="apiKey" value="sf_789b71c9e3edd05e34e6360f">
            <input type="hidden" name="replyTo" value="@">
            <input type="text" name="honeypot" style="display:none">

            <button type="submit" id="submitBtn">Send Message</button>
        </form>
    </div>

    <script>
        const form = document.getElementById('contactForm');
        const submitBtn = document.getElementById('submitBtn');
        const alertBox = document.getElementById('alertBox');

        form.addEventListener('submit', async function(e) {
            e.preventDefault();

            // Disable submit button
            submitBtn.disabled = true;
            submitBtn.textContent = 'Sending...';

            // Hide any previous alerts
            alertBox.classList.remove('show', 'alert-success', 'alert-error');

            try {
                const formData = new FormData(form);
                const data = Object.fromEntries(formData);

                const response = await fetch('https://api.staticforms.dev/submit', {
                    method: 'POST',
                    body: JSON.stringify(data),
                    headers: { 'Content-Type': 'application/json' }
                });

                const result = await response.json();

                if (result.success) {
                    // Show success message
                    alertBox.textContent = 'Thank you! Your message has been sent successfully. We\'ll get back to you soon.';
                    alertBox.classList.add('alert-success', 'show');

                    // Reset form
                    form.reset();
                } else {
                    throw new Error(result.message || 'Something went wrong');
                }
            } catch (error) {
                // Show error message
                alertBox.textContent = 'Oops! Something went wrong. Please try again.';
                alertBox.classList.add('alert-error', 'show');
            } finally {
                // Re-enable submit button
                submitBtn.disabled = false;
                submitBtn.textContent = 'Send Message';
            }
        });
    </script>
</body>
</html>

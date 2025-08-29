# 7-Fig-Builder-Landing-Page
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>7 Figure Builder</title>
    <style>
        /* CSS Reset */
        *, *::before, *::after { box-sizing: border-box; }
        body, h1, h2, h3, p, figure, blockquote, dl, dd { margin: 0; }
        html, body { overflow-x: hidden; }

        /* Global Styles */
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
            line-height: 1.6;
            background-color: #0B0F19;
            color: #E0E0E0;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        .container {
            width: 100%;
            max-width: 800px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Typography */
        h1, h2, h3 {
            font-weight: 800;
            line-height: 1.2;
            color: #FFFFFF;
            margin-bottom: 1rem;
        }

        h1 { font-size: clamp(2.5rem, 6vw, 4rem); }
        h2 { font-size: clamp(2rem, 5vw, 3rem); text-align: center; }
        h3 { font-size: clamp(1.5rem, 4vw, 2rem); }

        p {
            font-size: clamp(1rem, 2.5vw, 1.2rem);
            margin-bottom: 1.5rem;
            max-width: 650px;
        }

        b, strong { font-weight: 700; color: #FFFFFF; }

        /* Sections */
        .section {
            padding: clamp(40px, 10vw, 100px) 0;
            border-bottom: 1px solid #2A2F3A;
        }

        .section-center {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
        }
        
        .section-center p {
            margin-left: auto;
            margin-right: auto;
        }

        /* Hero Section */
        .hero {
            background: radial-gradient(ellipse at top, #1D2434, #0B0F19);
            text-align: center;
            padding-top: clamp(30px, 8vw, 60px);
        }

        .preheader {
            font-size: 1rem;
            font-weight: 600;
            color: #4A90E2;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            margin-bottom: 1rem;
        }

        .hero h1 {
            text-shadow: 0px 4px 20px rgba(0, 0, 0, 0.3);
        }

        .hero .subheader {
            font-size: clamp(1.1rem, 3vw, 1.3rem);
            color: #A0AEC0;
            max-width: 600px;
            margin: 1.5rem auto 2rem;
        }

        .vsl-container {
            max-width: 700px;
            width: 100%;
            margin: 2rem auto;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            position: relative;
            cursor: pointer;
        }

        .vsl-thumbnail {
            width: 100%;
            height: auto;
            display: block;
        }

        .play-button {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80px;
            height: 80px;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: transform 0.2s ease, background-color 0.2s ease;
        }
        
        .vsl-container:hover .play-button {
            transform: translate(-50%, -50%) scale(1.1);
            background-color: white;
        }

        .play-icon {
            width: 0;
            height: 0;
            border-top: 15px solid transparent;
            border-bottom: 15px solid transparent;
            border-left: 25px solid #0B0F19;
            margin-left: 5px;
        }

        /* CTA Button */
        .cta-button {
            display: inline-block;
            background: linear-gradient(90deg, #F5A623, #FF7E5F);
            color: #0B0F19;
            font-size: 1.25rem;
            font-weight: 700;
            padding: 18px 35px;
            border-radius: 8px;
            text-decoration: none;
            text-align: center;
            box-shadow: 0 5px 15px rgba(245, 166, 35, 0.4);
            transition: transform 0.2s ease, box-shadow 0.2s ease;
            margin-top: 1rem;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(245, 166, 35, 0.5);
        }
        
        .cta-subtext {
            font-size: 0.9rem;
            color: #A0AEC0;
            margin-top: 10px;
        }

        /* Fascination Headlines */
        .fascination-headline {
            font-size: 1.1rem;
            font-weight: 600;
            color: #4A90E2;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 2rem;
        }

        /* Bullet Points */
        .bullet-list {
            list-style: none;
            padding: 0;
            max-width: 650px;
            text-align: left;
            margin: 2rem auto;
        }

        .bullet-list li {
            display: flex;
            align-items: flex-start;
            font-size: 1.1rem;
            margin-bottom: 1.5rem;
        }

        .bullet-icon {
            color: #F5A623;
            font-size: 1.5rem;
            margin-right: 15px;
            flex-shrink: 0;
            margin-top: 2px;
        }
        
        /* FAQ Section */
        .faq-item {
            background-color: #161B27;
            border: 1px solid #2A2F3A;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 1rem;
            text-align: left;
            max-width: 700px;
            width: 100%;
        }
        
        .faq-item h3 {
            margin-bottom: 0.5rem;
            color: #F5A623;
        }
        
        .faq-item p {
            margin-bottom: 0;
            color: #A0AEC0;
        }

        /* Media Queries */
        @media (max-width: 768px) {
            .container { padding: 0 15px; }
            .section { padding: 60px 0; }
        }
    </style>
</head>
<body>

    <!-- HERO SECTION -->
    <header class="hero section">
        <div class="container">
            <p class="preheader">For Full-Time Professionals & Skilled Trades</p>
            <h1>Build and Sell a House for $100,000+ Profit in Your First Year…</h1>
            <p class="subheader">Using a 7-step virtual system that works from your laptop—even if you have zero building experience and want to keep your 9-to-5 job.</p>

            <!-- VSL Placeholder -->
            <div class="vsl-container">
                <img src="https://placehold.co/1280x720/1D2434/FFFFFF?text=Click+To+Play" alt="Video presentation thumbnail" class="vsl-thumbnail" onerror="this.onerror=null;this.src='https://placehold.co/1280x720/1D2434/FFFFFF?text=Video+Unavailable';">
                <div class="play-button">
                    <div class="play-icon"></div>
                </div>
            </div>

            <a href="#offer" class="cta-button">BOOK A CALL WITH OUR TEAM</a>
            <p class="cta-subtext">Spots are limited. Secure your free strategy session now.</p>
        </div>
    </header>

    <!-- PROBLEM IDENTIFICATION -->
    <section class="section section-center">
        <div class="container">
            <p class="fascination-headline">Does This Sound Familiar?</p>
            <h2>You're Stuck Trading Hours for Dollars, and Your "Safe" 9-to-5 Feels More Like a Cage.</h2>
            <p>You do good work. You get paid well. But that feeling in your gut doesn't go away.</p>
            <p>The one that says, "Is this it?"</p>
            <p>You know you're capable of more. You see other people building real wealth in real estate, but it feels like a private club you weren't invited to.</p>
            <p>You've probably thought about it... maybe even browsed Zillow, watched some flipping shows on TV, or talked to an agent who made it all sound impossibly complicated and expensive.</p>
            <p>They tell you need a ton of capital, a contractor's license, and all the free time in the world.</p>
            <p>So you stay put. You keep trading your life's most valuable asset—your time—for a paycheck that barely moves the needle. All while the cost of everything keeps going up.</p>
            <p>Doing nothing isn't just costing you money. It's costing you freedom.</p>
        </div>
    </section>

    <!-- ORIGIN STORY -->
    <section class="section section-center">
        <div class="container">
            <p class="fascination-headline">Our Story</p>
            <h2>We Generated $793,000 in 8 Months Across 17 States... Without Ever Swinging a Hammer.</h2>
            <p>We're Ruben and Arthur. And not long ago, we were exactly where you are.</p>
            <p>We were working professionals, tired of the corporate grind and the illusion of security. We craved control over our financial future.</p>
            <p>We dove into real estate headfirst and quickly learned the hard way: the traditional system is broken. It's designed to benefit agents, brokers, and big-money investors—not regular people like us.</p>
            <p>We made costly mistakes. We trusted the wrong people. We almost gave up.</p>
            <p>But instead of quitting, we got systematic. We asked, "What if we could create a repeatable process? A checklist-driven system that removes the guesswork, the gatekeepers, and the need to be physically on-site?"</p>
            <p>We spent years refining a 7-step method that allowed us to find lots, underwrite deals, manage construction, and sell homes for massive profits... all from our laptops.</p>
            <p>The result? We built over 220 homes in 4 years. And we did it while others were stuck waiting for the "perfect" deal that never comes.</p>
        </div>
    </section>

    <!-- SOLUTION REVELATION -->
    <section class="section section-center">
        <div class="container">
            <p class="fascination-headline">The 7-Step System</p>
            <h2>The "Virtual Builder" Method To Add Six Figures To Your Income This Year.</h2>
            <p>This isn't about theory. It's a field-tested, step-by-step process for building and selling a home for profit. Virtually.</p>
            <p>It’s a system built on 7 core pillars:</p>
            <ul class="bullet-list">
                <li>
                    <span class="bullet-icon">1.</span>
                    <div>
                        <strong>Lead Flow Automation:</strong> Get a consistent stream of off-market lot opportunities sent directly to you, so you're never competing with the masses on the MLS. You become the deal-finder, not the deal-chaser.
                    </div>
                </li>
                <li>
                    <span class="bullet-icon">2.</span>
                    <div>
                        <strong>Locking Up a Deal:</strong> Use our word-for-word scripts and negotiation templates to get sellers to say "yes" to your terms, giving you control of a property with minimal upfront risk.
                    </div>
                </li>
                <li>
                    <span class="bullet-icon">3.</span>
                    <div>
                        <strong>Selling the Deal:</strong> The secret to making money before you even build. We show you how to secure a buyer and lock in your profit, creating an average margin of $20,000 per deal.
                    </div>
                </li>
                <li>
                    <span class="bullet-icon">4.</span>
                    <div>
                        <strong>Finding a Lot:</strong> A simple, data-driven process for identifying the perfect plot of land, ensuring your project is profitable from day one.
                    </div>
                </li>
                <li>
                    <span class="bullet-icon">5.</span>
                    <div>
                        <strong>Underwriting Like a Pro:</strong> Our plug-and-play Excel calculators do the heavy lifting. Confidently analyze any deal in minutes to know exactly what your costs and profits will be. You become a sharp investor who never overpays.
                    </div>
                </li>
                <li>
                    <span class="bullet-icon">6.</span>
                    <div>
                        <strong>Construction Management (From a Distance):</strong> Navigate permits, find reliable contractors, and manage the entire build process without setting foot on the job site. You become the project manager, not the laborer.
                    </div>
                </li>
                 <li>
                    <span class="bullet-icon">7.</span>
                    <div>
                        <strong>The Sales Process:</strong> Proven strategies to market and sell your finished home for top dollar, putting a six-figure check in your bank account.
                    </div>
                </li>
            </ul>
        </div>
    </section>

    <!-- PRODUCT INTRODUCTION -->
    <section class="section section-center">
        <div class="container">
            <p class="fascination-headline">Your Path to Financial Control</p>
            <h2>Introducing The 7 Figure Builder Accelerator</h2>
            <p>This is more than a course. It's a complete implementation program designed to give you every tool, template, and system you need to go from zero experience to your first profitable home build.</p>
            <p>Forget the confusing books and hyped-up gurus. We've bottled our entire multi-million dollar operation into a system you can follow.</p>
            <p>No more guessing what to do next. No more fear of making a costly mistake. Just a clear, step-by-step path to building a new, high-income skill that can secure your family's future.</p>
        </div>
    </section>

    <!-- OFFER STRUCTURE -->
    <section id="offer" class="section section-center" style="background-color: #161B27;">
        <div class="container">
            <p class="fascination-headline">Take Action</p>
            <h2>Here's What To Do Next</h2>
            <p>This isn't for everyone. We're looking for action-takers who are serious about changing their financial situation.</p>
            <p>If that's you, the next step is to book a free, no-obligation strategy call with our team.</p>
            <p>On this call, we will personally map out a custom 7-step plan for you based on your specific situation and goals. You'll walk away with a clear roadmap for your first profitable build.</p>
            <p>We only open a handful of these spots each week to ensure we can provide dedicated attention to each person. They fill up fast.</p>
            <a href="#offer" class="cta-button">BOOK YOUR FREE STRATEGY CALL NOW</a>
            <p class="cta-subtext">Find out if the 7 Figure Builder system is right for you.</p>
        </div>
    </section>

    <!-- FAQ SECTION -->
    <section class="section section-center">
        <div class="container">
            <p class="fascination-headline">Your Questions, Answered</p>
            <h2>What You Might Be Thinking...</h2>
            
            <div class="faq-item">
                <h3>"But I have zero building or real estate experience. Can I really do this?"</h3>
                <p>This system was specifically designed for you. It's a paint-by-numbers process that removes the need for prior experience. We give you the scripts, the calculators, and the step-by-step checklists so you can operate with the confidence of a seasoned pro from day one.</p>
            </div>
            
            <div class="faq-item">
                <h3>"I have a demanding full-time job. How much time does this take?"</h3>
                <p>This was built for people with jobs. The entire system is designed to be managed virtually in your spare time. If you have a few hours a week to focus, you can get this done. It's about working smart, not hard, using our automated systems and processes.</p>
            </div>

            <div class="faq-item">
                <h3>"This sounds great, but how do I know I can trust you guys?"</h3>
                <p>We've built over 220 homes in 4 years and personally generated $793,000 in assignment fees in just 8 months across 17 states. We're not teaching theory; we're giving you the exact playbook we use every single day in our own business. The numbers speak for themselves.</p>
            </div>

            <div class="faq-item">
                <h3>"What if I get stuck? What kind of support is there?"</h3>
                <p>You're not alone. When you join, you get access to our community of fellow builders and our team. On your initial call, we'll explain the full support system, but rest assured, we're here to help you succeed.</p>
            </div>
            
            <div class="faq-item">
                <h3>"Is this going to be really expensive?"</h3>
                <p>Think about the cost of inaction. Another year of trading time for money. Another year of watching others build wealth while you sit on the sidelines. Your call is completely free. We'll show you the plan, and you can decide if the investment in yourself is worth the potential of a six-figure return in your first year.</p>
            </div>
            
            <div style="margin-top: 40px;">
                <a href="#offer" class="cta-button">BOOK MY FREE CALL & GET THE PLAN</a>
                <p class="cta-subtext">It's time to take control. Let's build.</p>
            </div>
        </div>
    </section>

</body>
</html>

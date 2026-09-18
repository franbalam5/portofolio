---
title: "MCyRA 2026 Official Conference Website"
date: 2025-06-20
description: "Architecture, responsive UI engineering, and deployment for the Mexican Conference on Cybersecurity Research and Applications (UNAM)."
icon: "fa-solid fa-globe"
accent: "cyan"
status: "completed"
tags: ["react", "tailwind", "vite", "frontend", "ui-ux"]
draft: false
---

# MCyRA 2026 Conference Platform

Lead frontend development for the official web portal of the **Mexican Conference on Cybersecurity Research and Applications (MCyRA 2026)**, hosted at UNAM. The initiative modernized a legacy academic presence into a high-performance, mobile-first web app serving international researchers, speakers, and authors.

![MCyRA 2026 website](/images/projects/amw2026-preview.png)
*Production UI featuring dynamic theme switching, responsive navigation, and contextual registration flows.*

---

### Project Scope & Role

I served as the core frontend developer for the initial launch phase (my active contribution concluded with the delivery of the base release and submission systems). Working in collaboration with the conference organizing committee, I handled the architectural design, component modularization, and responsive UI implementation.

**Core Contributions:**
* **Design System & Visual Architecture:** Built a modular UI using React and Tailwind CSS featuring integrated Dark/Light modes, custom typography hierarchies, and SVG asset pipelines.
* **Complex Academic Workflows:** Engineered custom views for the *Call for Papers (LNCS / CCIS standards)*, *Call for Tutorials*, and *Call for Student Consortium* tracking deadlines and submission guidelines.
* **Dynamic SaaS-Style Registration:** Developed multi-tiered pricing matrices (Authors vs. Students, Early vs. Late rates) with contextual modal overlays.
* **Zero-Backend Data Ingestion:** Integrated embedded, dynamic-height Tally form workflows inside React modals to securely capture proof-of-payment files, billing metadata, and student credentials without exposing the institutional server to file-upload exploits.
* **Institutional Deployment:** Developed and previewed via Vite + Vercel before handing off a production build optimized for deployment on UNAM's institutional web servers.

---

### Technical Challenges & Solutions

| Challenge | Solution |
| :--- | :--- |
| **High Information Density** | Segmented dense CFPs, dual-track dates, and formatting rules into collapsible mobile-friendly drawers and scannable cards. |
| **Iframe Theme Collisions** | Resolved embedded form color-inversion issues across OS dark-mode preferences by programmatically neutralizing parent backgrounds and handling viewport resizes via runtime script hooks. |
| **Zero-Friction Registration** | Decoupled fee calculations from form inputs by passing URL query parameters directly into the modal embed, automatically tagging attendee categories without backend code. |

---

### Tech Stack

* **Core:** React 18, Vite
* **Styling:** Tailwind CSS, Lucide Icons / Heroicons
* **Integrations:** Tally Forms API (Headless embed), Microsoft CMT portal bridges
* **Deployment:** UNAM Institutional Infrastructure (Production), Vercel (Staging)
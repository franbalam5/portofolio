---
title: "CEDIVIPA: Modernization & Educational Ecosystem"
date: 2024-11-10
description: "Architectural modernization of UNAM's oral telepathology platform and development of an interactive gamified learning ecosystem (PAPIME)."
icon: "fa-solid fa-tooth"
accent: "rose"
status: "active"
tags: ["php", "mariadb", "javascript", "mvc", "tailwind", "gamification"]
draft: false
---

# CEDIVIPA: Oral Pathology Teleconsultation & Learning Platform

Originally established in 2011 at UNAM's Faculty of Dentistry, CEDIVIPA provides free asynchronous diagnostic interconsultations for complex maxillofacial lesions, having resolved over 2,750 clinical cases. 

This project focused on modernizing the legacy monolithic architecture into a secure MVC system, while engineering an interactive gamified learning ecosystem backed by the PAPIME educational initiative.

![CEDIVIPA platform preview](/images/projects/cedivipa-dashboard.png)
*Modernized clinical case management and educational workspace.*

---

### Key Contributions & Features

- **Architectural Overhaul & RBAC Security:** Refactored a 15-year legacy PHP monolith into a modular MVC architecture (PHP 8 / MariaDB). Implemented strict Role-Based Access Control to decouple confidential patient biometric/photographic records from public and educational interfaces across 4 distinct user profiles.
- **Cognitive-Mapped Gamification (PAPIME):** Designed and implemented client-side interactive modules mapped directly to dental diagnostic skills:
  - *Crosswords:* Reinforcing semantic association between symptoms and histopathological entities.
  - *Word Searches:* Training visual discrimination and selective attention for medical records.
  - *Quizzes:* Exercising active retrieval practice under controlled time constraints.
- **Asynchronous Telemetry Engine:** Built high-precision tracking using `performance.now()` and asynchronous `Fetch API` pipelines, transmitting sub-second timing deltas, attempts, and conceptual failure patterns without page reloads or UI blocking.
- **Docent Analytics Dashboard:** Created an aggregated analytical control panel enabling professors to upload/categorize infographics independently and monitor weak diagnostic concepts by pathological category, prioritizing pedagogical diagnosis over punitive evaluation.

### Tech Stack

- **Backend:** PHP 8 (Modular MVC architecture), Apache.
- **Database:** MariaDB (Normalized relational schema, ACID transactional persistence).
- **Frontend:** Vanilla JavaScript (ES6 DOM manipulation & asynchronous Fetch API), HTML5.
- **Styling:** Hybrid layout leveraging Tailwind CSS utility classes and Bootstrap UI components.
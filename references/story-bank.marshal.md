# Story Bank

The raw material your posts are made of: what you have actually done, in numbers,
with names and dates. The Voice Profile holds *how you sound*. This holds *what
you have to say*.

## Status

- filled: yes
- updated: 2026-11-04
- author: Marshal Alone
- target: Entry-level / Fresher Java Backend / Software Developer opportunities

---

## 1. Timeline

- **2022 – 2026**: B.Tech in Computer Science and Engineering at RTMNU Nagpur (CGPA: 8.0/10).
- **Recent – Present**: Java Full Stack Development training at QSpiders, Wakad, Pune.
  - Core Java (OOP principles, Collections Framework, Exception Handling).
  - Web fundamentals (HTML5, CSS3, JavaScript, SQL/Relational Databases).
  - Upcoming: Advanced Java (Enterprise / Spring / Backend frameworks).
- **Self-directed learning (Present)**: Full stack JavaScript (Node.js, Express.js, MongoDB) and DevOps infrastructure on AWS.

## 2. Receipts

- **8.0 / 10 CGPA**: Graduating in Computer Science & Engineering (RTMNU Nagpur, 2026).
- **Dual-channel delivery**: Built `Mail-E` using `Promise.allSettled()` to deliver notifications simultaneously via Telegram Bot API and local Android SMS Gateway over Wi-Fi without blocking or cascading failure.
- **5 DevOps servers on AWS**: Set up and configured Maven, Jenkins, SonarQube, JaCoCo code coverage, and Nexus repository manager instances.
- **State-level Hackathon**: Selected at NIRMAN Hackathon for designing a digital farmer machinery rental platform (`FarmRent`).
- **Productivity tool**: Built `ApplicationTracker` (Chrome extension + Node.js/MongoDB) to scrape and organize job applications directly from job portals via DOM scripts.

## 3. Shipped

- **Mail-E**: Campus recruitment notification web app. Uses Node.js and Express to push updates. Key technical highlight: Integrated an open-source Android SMS Gateway over local Wi-Fi with Basic Auth, dual-SIM routing, and `AbortSignal` timeouts.
- **FarmRent**: Machinery sharing platform for farmers. Implemented secure authentication, session management, and validation logic with Express and MongoDB.
- **ApplicationTracker**: Chrome extension capturing job application metadata directly from job portal DOM trees on click, piped into a custom Node.js/Express dashboard.

## 4. Turning points

- **Moving from "tutorial code" to system architecture**: Realizing that writing basic Java syntax is easy, but understanding how code gets tested (JaCoCo), analyzed for code smells (SonarQube), artifacted (Nexus), and automated (Jenkins) is what separates a student from a production-ready engineer.
- **Handling asynchronous failure in Mail-E**: Originally thought simple `Promise.all()` was fine, until an SMS network timeout broke the entire notification batch. Replaced it with `Promise.allSettled()` and `AbortSignal` timeouts, learning that distributed systems must fail gracefully and independently.

## 5. Scars

- **Wi-Fi latency and SMS Gateway timeouts**: Local Android Wi-Fi SMS gateway would intermittently hang when the phone went to low-power state. Fixed it by implementing strict `AbortSignal` timeouts and fallback logging so student notifications were never lost silently.
- **EC2 security groups and permissions**: First time setting up Jenkins, SonarQube, and Nexus on AWS, struggled with port routing, memory constraints on small instances, and service conflicts. Learned Linux systemd process management and port configuration the hard way.

## 6. Positions

- **A fresher shouldn't just know how to write code; they must understand how code reaches production.** Setting up a CI/CD pipeline on AWS taught me more about software engineering than solving 100 generic LeetCode problems.
- **Dual-stack curiosity makes you a better backend engineer.** Starting with Java OOP, but exploring Node.js event-driven architecture and asynchronous I/O makes you appreciate multithreading vs event loops at a deeper level.

## 7. Recurring stories

- Setting up an entire CI/CD pipeline from scratch on AWS EC2: Maven build -> SonarQube quality gate -> JaCoCo test coverage -> Nexus artifact repository -> Jenkins automation.
- Solving the real-world notification drop issue in Mail-E using `Promise.allSettled()` and `AbortSignal` over a local Android SMS gateway.

## 8. Names you can use

- Free to name: QSpiders Wakad, RTMNU Nagpur, AWS, Jenkins, SonarQube, JaCoCo, Nexus, Maven, Node.js, Express, MongoDB, Core Java, Telegram Bot API.

## 9. Off limits

- Unverified metrics, exaggerated years of experience, claiming complete mastery of frameworks not yet studied (e.g. Advanced Java is still upcoming, so stay honest about what is completed vs what is currently being learned).

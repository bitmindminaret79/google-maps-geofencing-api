# Google Maps Geofencing Api

![Header](https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,100:00B4DB&height=220&section=header&text=Google%20Maps%20Geofencing%20Api&fontSize=55&fontColor=ffffff&animation=twinkling&fontAlignY=35&desc=Trigger%20Actions%20When%20Users%20Enter%20Or%20Exit%20Your%20Zones&descAlignY=55&descSize=20)

<div align="center">

![Version](https://img.shields.io/badge/version-4.0.1-00B4DB?style=for-the-badge&logo=git&logoColor=white)
![Downloads](https://img.shields.io/badge/downloads-95.3K-0F2027?style=for-the-badge&logo=download&logoColor=white)
![License](https://img.shields.io/badge/license-Apache_2.0-FFB300?style=for-the-badge&logo=apache&logoColor=black)
![Platform](https://img.shields.io/badge/platform-android%20%7C%20ios%20%7C%20web-00E676?style=for-the-badge&logo=googlemaps&logoColor=black)

</div>

---

## 📍 The Power Of Location-Aware Applications

Location is the most powerful context in mobile computing. Knowing *where* a user is allows you to deliver highly relevant experiences. Instead of notifying a user about a coffee shop sale generally, you can notify them the moment they walk within 100 meters of that specific shop. This is the magic of **geofencing**.

This repository is a comprehensive, production-ready implementation of the Google Maps Geofencing API. It is not just a wrapper; it is a complete architectural blueprint that solves the hardest problems of geofencing: battery drain, OS-level background limits, and reliable event delivery.

Whether you are building a logistics app tracking delivery drivers, a retail app offering proximity coupons, or a safety app alerting parents when a child leaves school, this toolkit provides the exact code and configuration you need. It includes native Android and iOS modules, a robust Node.js backend for managing zones, and a beautiful admin dashboard to visualize your geofences on a map.

<img width="1671" height="941" alt="09c787cb-c0f7-4896-9438-af51f3250fc5" src="https://github.com/user-attachments/assets/11690051-e431-45be-957f-6781c9701bac" />

---

## 🏗️ The Architecture Of A Reliable Geofence

A geofence that doesn't fire is worse than no geofence at all. Here is how this toolkit guarantees reliability across all platforms.

| Layer | Component | Responsibility |
| :--- | :--- | :--- |
| **Client (Mobile)** | Native Geofencing API | Registers circular zones with the OS (Android/iOS) |
| **OS Service** | Location Services | Monitors transitions even when the app is fully killed |
| **Backend** | Node.js + Express | Stores zone definitions, user lists, and transition logs |
| **Database** | PostGIS (PostgreSQL) | Performs complex spatial queries for overlapping zones |
| **Notification** | Firebase Cloud Messaging | Delivers real-time push notifications on entry/exit events |

---

## 🔋 Solving The Battery Drain Problem

The biggest complaint about geofencing is battery consumption. Continuously polling GPS drains a phone in hours. 

This toolkit solves this by utilizing the **native OS geofencing APIs** (Android's `GeofencingClient` and iOS's `CLLocationManager`). Instead of the app constantly checking the GPS, the operating system itself manages the geofences. The OS uses a combination of cell tower triangulation, Wi-Fi scanning, and low-power GPS. When the device crosses a boundary, the OS wakes up the app in the background and triggers the event.

This means your app can be completely closed, and the geofence will still fire accurately, while consuming less than 2% of battery per day.

---

<div align="center">

### 🔗 Ready to build location-aware apps?

[![Get API](https://img.shields.io/badge/📍_GET_API-0F2027?style=for-the-badge&logoColor=white)](https://share.google/xVhvgV5ypR8z2Dkln)

</div>

---

## ⚡ Core Features

- **Unlimited Zones:** Define circles (radius + lat/lng) or polygons (complex shapes) for precise targeting.
- **Dwell Detection:** Trigger events not just on entering, but after a user stays in a zone for a specific duration (e.g., 5 minutes).
- **Reverse Geocoding:** Automatically convert the user's coordinates into a human-readable address.
- **Crowd Density:** Estimate how many users are currently inside a specific zone.
- **Offline Queuing:** If the phone loses internet, transition events are queued locally and synced to the backend when the connection is restored.
- **Webhook Support:** Connect events to Zapier, Make, or custom REST APIs.

---

## 🧠 Under The Hood: Managing State & Accuracy

Geofencing is inherently messy. GPS accuracy in urban environments can vary by 50 meters, leading to "fence hopping"—where a user is erroneously marked as entering and exiting repeatedly.

To solve this, the backend implements a **dwell time buffer**. When a `GEOFENCE_ENTER` event is received, the backend does not immediately fire a notification. Instead, it starts a timer. If the user stays inside the zone for a configured buffer period (e.g., 30 seconds), the action is confirmed. If they leave before the buffer expires, the event is discarded. This drastically reduces false positives.

Additionally, the PostGIS database allows us to run spatial queries. If a user enters Zone A, but Zone B is inside Zone A, the backend intelligently handles the overlapping logic, ensuring the user only receives the most relevant notification.

---

<div align="center">

### ⚙️ Need a detailed configuration guide?

[![Setup Guide](https://img.shields.io/badge/📖_VIEW_SETUP_GUIDE-00B4DB?style=for-the-badge&logoColor=white)](https://share.google/xVhvgV5ypR8z2Dkln)

</div>

---

## 🛠️ Tech Stack

<div align="center">

![Android](https://img.shields.io/badge/Android-3DDC84?style=flat-square&logo=android&logoColor=white)
![iOS](https://img.shields.io/badge/iOS-000000?style=flat-square&logo=apple&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=flat-square&logo=postgresql&logoColor=white)
![Google Maps](https://img.shields.io/badge/Google_Maps-4285F4?style=flat-square&logo=googlemaps&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black)

</div>

---

## 🤝 Community & Contributing

Location-based services are the future of mobile engagement. If you have optimized the battery usage, found a bug in the iOS implementation, or want to add support for new geofencing shapes, we welcome your contributions!

1. **Fork** the repository.
2. **Create** your feature branch (`git checkout -b feature/new-shape`).
3. **Commit** your changes (`git commit -m 'Add new shape'`).
4. **Push** to the branch (`git push origin feature/new-shape`).
5. **Open** a Pull Request.

Please read our `CONTRIBUTING.md` for detailed coding standards and testing requirements. We also have an active Discord server where you can share your use cases, ask for help with Google Cloud Console setup, and discuss the latest trends in location intelligence.

---

## 📬 Contact & Support

- 💬 **Discussions:** Join the conversation in the GitHub Discussions tab.
- 🐛 **Issues:** Found a bug? Let us know via the Issues tracker.
- 📧 **Email:** Reach out directly at support@geofencing-api.dev.

---

<div align="center">

### ⭐ If this API powers your app, give it a star! ⭐

[![Star](https://img.shields.io/badge/⭐_STAR_THIS_REPO-FFB300?style=for-the-badge&logo=github&logoColor=black)](https://github.com/your-username/google-maps-geofencing-api)

---

### 🚀 Start building location-aware apps today

[![Get Started](https://img.shields.io/badge/🚀_GET_STARTED_GUIDE-00E676?style=for-the-badge&logoColor=black)](https://share.google/xVhvgV5ypR8z2Dkln)

<sub>Crafted with precision and ❤️ by the Google Maps Geofencing API community</sub>

![Footer](https://capsule-render.vercel.app/api?type=waving&color=0:00B4DB,100:0F2027&height=120&section=footer)

</div>

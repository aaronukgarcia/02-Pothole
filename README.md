# PotholeWatch

**Open-Source Road Surface Monitoring Pilot**

A crowdsourced road surface monitoring system using Firebase, designed as a proof-of-concept for UK local councils.

> ⚠️ **Pilot Phase Only** — This is a technical feasibility study, not a production-ready system.

## Overview

PotholeWatch explores the technical feasibility of crowdsourced road surface monitoring. It provides a web form for citizens to report road defects with GPS coordinates, automatic clustering of nearby reports, and a read-only API for council GIS integration.

### What This Is

- A technical proof-of-concept for one local council pilot
- A demonstration of Firebase geospatial capabilities
- An exploration of data collection workflows
- A starting point for community discussion

### What This Is NOT

- A production-ready system
- A replacement for existing municipal asset management systems
- A guarantee of OEM cooperation or data access

## Tech Stack

| Component | Technology |
|-----------|------------|
| Database | Firebase Firestore (GeoHash for clustering) |
| Compute | Cloud Functions (Node.js) |
| Storage | Cloud Storage (images, max 5MB) |
| Email | SendGrid (transactional) |

## Features

- GPS-enabled location capture via map picker or device
- Optional photo upload (max 5MB)
- Automatic clustering of reports within 10m radius
- Email confirmation with reference number
- Read-only GeoJSON API for council integration
- reCAPTCHA v3 spam prevention

## API Endpoints

### POST /v1/reports
Submit a new pothole report.
- Authentication: reCAPTCHA v3
- Rate limit: 10 requests/hour per IP

### GET /v1/potholes
Retrieve pothole data (council access only).
- Authentication: API key
- Response: GeoJSON FeatureCollection
- Filters: Bounding box, date range, status

## Installation

```bash
# Clone the repository
git clone https://github.com/aaronukgarcia/02-Pothole.git
cd 02-Pothole

# Install dependencies
npm install

# Configure Firebase
firebase login
firebase init

# Deploy
firebase deploy
```

## Configuration

Create a `.env` file with the following variables:

```env
FIREBASE_PROJECT_ID=your-project-id
SENDGRID_API_KEY=your-sendgrid-key
RECAPTCHA_SECRET=your-recaptcha-secret
```

## Data Model

### Report Document
```json
{
  "id": "UUID",
  "timestamp": "ISO 8601 UTC",
  "location": "GeoPoint",
  "userEmail": "encrypted",
  "photoUrl": "Cloud Storage path",
  "intensity": "float (0-10)"
}
```

## Known Limitations

- **No native geospatial joins** — Uses GeoHash workaround
- **Cold start latency** — 1-3 seconds on first request
- **Firebase vendor lock-in** — No migration path specified
- **GDPR compliance** — Requires legal review and DPIA completion

## Contributing

Contributions are welcome. Please read the feasibility study document for context on scope and limitations before submitting PRs.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add improvement'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

## License

MIT License

Copyright (c) 2025 PotholeWatch Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Contact

- **Email:** aaron@garcia.ltd
- **GitHub:** [aaronukgarcia/02-Pothole](https://github.com/aaronukgarcia/02-Pothole)

---

*Honest Assessment. Realistic Scope. Clear Exit Plan.*

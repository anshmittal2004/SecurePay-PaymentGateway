# SecurePay Payment Gateway

A secure payment gateway built with React and Flask, featuring card type detection, fraud prevention, and PDF receipt generation.

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![React](https://img.shields.io/badge/React-18.0+-61DAFB.svg?logo=react)](https://reactjs.org/)
[![Flask](https://img.shields.io/badge/Flask-2.0+-000000.svg?logo=flask)](https://flask.palletsprojects.com/)

## Features

- **Multi-Card Support**: Visa, Mastercard, American Express, RuPay, Discover, JCB, Diners Club
- **Real-time Card Detection**: Automatic card type identification
- **Fraud Detection**: Flags suspicious transactions and patterns
- **PDF Receipts**: Professional receipt generation
- **Secure Processing**: SHA-256 card number hashing
- **Responsive Design**: Works on desktop and mobile

## Tech Stack

**Frontend:**
- React with Vite
- Lucide React (icons)
- jsPDF (PDF generation)
- CSS with Glassmorphism

**Backend:**
- Flask (Python)
- SQLite database
- SHA-256 encryption

## Installation

### Prerequisites
- Node.js 16+
- Python 3.8+

### Quick Start

```bash
# Clone repository
git clone https://github.com/anshmittal2004/SecurePay-PaymentGateway.git
cd SecurePay-PaymentGateway

# Frontend setup
cd Secure
npm install
npm run dev

# Backend setup (new terminal)
cd backend
pip install -r requirements.txt
python app.py
```

**Access:**
- Frontend: http://localhost:5173
- Backend: http://localhost:5000

## Project Structure

```
SecurePay-PaymentGateway/
├── Secure/                    # React frontend
│   ├── src/
│   │   ├── components/
│   │   │   ├── TransactionForm.jsx
│   │   │   └── TransactionDashboard.jsx
│   │   ├── utils/mockData.js
│   │   └── App.jsx
├── backend/                   # Flask backend
│   ├── app.py
│   ├── database.py
│   └── requirements.txt
```

## API Endpoints

### Process Payment
```http
POST /api/authorize
Content-Type: application/json

{
  "card_number": "4412345678901234",
  "amount": 1500.00,
  "name": "John Doe",
  "phone": "9876543210"
}
```

### Get Transactions
```http
GET /api/transactions
```

## Supported Cards

| Card Type | Pattern | Example |
|-----------|---------|---------|
| Visa | 4 | 4412 3456 7890 1234 |
| Mastercard | 51-55 | 5412 3456 7890 1234 |
| American Express | 34, 37 | 3412 345678 90123 |
| RuPay | 60, 65, 81, 82 | 6012 3456 7890 1234 |
| Discover | 6011, 644-649 | 6011 1234 5678 9012 |
| JCB | 3528-3589 | 3528 1234 5678 9012 |
| Diners Club | 30, 36, 38 | 3012 345678 9012 |

## Security Features

- **Card Encryption**: SHA-256 hashing before database storage
- **Fraud Detection**: 
  - High-value transactions (>₹10,000)
  - Rapid transactions from same card
  - Suspicious card patterns
- **Input Validation**: Comprehensive validation for all fields
- **No Plain Text Storage**: Card numbers never stored in plain text

## Testing

Use these test cards:

| Purpose | Card Number | Result |
|---------|-------------|--------|
| Valid Visa | 4412 3456 7890 1234 | Approved |
| Valid Mastercard | 5412 3456 7890 1234 | Approved |
| Fraud Detection | 0000 1234 5678 9012 | Flagged |

Run tests:
```bash
cd backend
python -m pytest tests/
```

## Future Enhancements

- PostgreSQL for production scalability
- OAuth authentication
- Rate limiting
- Multi-currency support
- Recurring payments
- Advanced analytics

## Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/new-feature`)
3. Commit changes (`git commit -m 'Add new feature'`)
4. Push to branch (`git push origin feature/new-feature`)
5. Open Pull Request

## License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## Author

**Ansh Mittal**
- GitHub: [@anshmittal2004](https://github.com/anshmittal2004)
- Project: [SecurePay Payment Gateway](https://github.com/anshmittal2004/SecurePay-PaymentGateway)

---

Built for secure, efficient payment processing with modern web technologies.

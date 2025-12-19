# Payment Processor

[![Build Status](https://img.shields.io/travis/your-username/payment-processor.svg?branch=main)](https://travis-ci.com/your-username/payment-processor)
[![Coverage Status](https://img.shields.io/codecov/c/github/your-username/payment-processor.svg)](https://codecov.io/gh/your-username/payment-processor)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

A robust and flexible payment processing library supporting multiple payment gateways.

## Features

*   **Multiple Gateway Support:** Integrates with Stripe, PayPal, and Braintree.
*   **Secure Transactions:** Implements industry-standard security practices for handling sensitive data.
*   **Subscription Management:** Supports creating, updating, and canceling subscriptions.
*   **Webhook Handling:** Provides a mechanism for handling asynchronous events from payment gateways.
*   **Detailed Logging:** Logs all transaction activities for auditing and debugging.
*   **Easy Integration:** Simple and well-documented API for seamless integration into your applications.
*   **Comprehensive Testing:** Thoroughly tested with unit and integration tests.

## Getting Started

### Prerequisites

*   Python 3.7+
*   A configured virtual environment (recommended)

### Installation

```bash
pip install payment-processor
```

### Configuration

Configure the payment processor by setting the necessary API keys and credentials for each gateway. You can do this using environment variables or a configuration file.

Example using environment variables:

```bash
export STRIPE_API_KEY="your_stripe_api_key"
export PAYPAL_CLIENT_ID="your_paypal_client_id"
export PAYPAL_CLIENT_SECRET="your_paypal_client_secret"
export BRAINTREE_MERCHANT_ID="your_braintree_merchant_id"
export BRAINTREE_PUBLIC_KEY="your_braintree_public_key"
export BRAINTREE_PRIVATE_KEY="your_braintree_private_key"
```

### Usage

```python
from payment_processor import PaymentProcessor
from payment_processor.gateways import StripeGateway, PayPalGateway

# Initialize the payment processor with the desired gateways
processor = PaymentProcessor(
    gateways=[
        StripeGateway(api_key="your_stripe_api_key"),
        PayPalGateway(client_id="your_paypal_client_id", client_secret="your_paypal_client_secret")
    ]
)

# Create a charge
try:
    charge = processor.create_charge(
        amount=10.00,
        currency="USD",
        source="tok_visa", # Stripe token or PayPal payment method id
        gateway="stripe", # or "paypal"
        description="Test charge"
    )
    print(f"Charge ID: {charge.id}")
    print(f"Charge Status: {charge.status}")
except Exception as e:
    print(f"Error creating charge: {e}")

# Create a customer (Stripe example)
try:
    customer = processor.create_customer(
        email="test@example.com",
        source="tok_visa", # Stripe token
        gateway="stripe",
        description="New Customer"
    )
    print(f"Customer ID: {customer.id}")
except Exception as e:
    print(f"Error creating customer: {e}")
```

## Documentation

Detailed documentation is available at [https://your-domain.com/payment-processor/docs](https://your-domain.com/payment-processor/docs).

## Contributing

We welcome contributions! Please see the [CONTRIBUTING.md](CONTRIBUTING.md) file for guidelines.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For support, please open an issue on GitHub or contact us at support@example.com.
# SweetSync - POS System

A web-based Point of Sale (POS) application built with Python (Flask) designed for a shop. It manages inventory, processes orders, records transaction history in Excel, and generates UPI QR codes for easy payments. It also features a real-time "Customer View" for mobile devices.

## 📋 Features

* **Inventory Management:** Add and remove items (Cakes/Pastries) easily via the dashboard. Data is persisted in `items.xlsx`.
* **Order Processing:** Select multiple items and quantities to calculate total costs automatically.
* **UPI Payment Integration:** Generates a dynamic UPI QR code for the specific order amount upon checkout.
* **Dual-Screen Support:**
    * **Admin/POS View:** For the shopkeeper to input orders.
    * **Mobile/Customer View:** A real-time display (using WebSockets) that shows the order summary and QR code on a secondary device or phone.
* **Transaction Logging:** Automatically saves all order details to `transaction_history.xlsx`.

## 🛠️ Technologies Used

* **Python** (Backend Logic)
* **Flask** (Web Framework)
* **Pandas** (Excel Data Management)
* **Flask-SocketIO** (Real-time updates)
* **Bootstrap 4** (Frontend Styling)
* **QRCode** (Payment generation)

## ⚙️ Installation

1.  **Clone the repository** (or download the source code).

2.  **Install Dependencies:**
    Ensure you have Python installed. It is recommended to use a virtual environment.
    ```bash
    pip install -r requirements.txt
    ```

3.  **Project Structure:**
    Ensure your directory looks like this:
    ```text
    /project-folder
    ├── app.py                 # Main application file
    ├── requirements.txt       # Python dependencies
    ├── favicon.png            # App icon
    └── templates/
        ├── index.html         # Admin dashboard
        ├── mobile.html        # Customer mobile view
        ├── order_summary.html # Order confirmation page
    ```

## 🚀 Usage

1.  **Start the Application:**
    Run the following command in your terminal:
    ```bash
    python app.py
    ```

2.  **Access the Dashboard (Shopkeeper):**
    Open your web browser and go to:
    `http://localhost:5000` (or `http://127.0.0.1:5000`)

3.  **Setup Customer Display (Optional):**
    To use the mobile view, connect your phone to the same Wi-Fi network as your computer. Find your computer's local IP address and navigate to:
    `http://<YOUR_LOCAL_IP>:5000/mobile`
    *As you place orders on the computer, this mobile screen will automatically update.*

## 📂 Data Management

* **Items:** The app will automatically create `items.xlsx` on the first run. You can add items via the web interface.
* **Transactions:** Sales are logged in `transaction_history.xlsx`, recording Customer Name, Plot Number, Items, and Cost.

## ⚠️ Configuration

**Changing the UPI ID:**
Currently, the UPI ID is set to `yourupi@bank.com`. To change this to your own merchant ID:

1.  Open `app.py`.
2.  Locate the `place_order` function (around line 83).
3.  Update the `pa` parameter in the `qr_data` string:
    ```python
    qr_data = f'upi://pay?pa=YOUR_UPI_ID&pn=YOUR_SHOP_NAME&am={total_cost}&cu=INR'
    ```

## 📝 License
Copyright (c) 2026 SweetSync-POS SYSTEM. All Rights Reserved.

This software is the confidential and proprietary information of Aarav Kumar.
Unauthorized copying of this file, via any medium is strictly prohibited.

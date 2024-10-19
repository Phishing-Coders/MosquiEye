# **MosquiEye – Smart Mosquito Monitoring**

**MosquiEye** is an AI-powered web and mobile application designed to automate the process of mosquito egg counting and visualize mosquito breeding hotspots using ovitrap data. The system provides Ministry of Health officers with real-time insights and analytics to enhance mosquito control efforts.

## **Project Overview**

MosquiEye leverages AI technology to detect and count mosquito eggs from images uploaded by field officers. It also integrates GPS data to display mosquito breeding hotspots on an interactive map, allowing for more efficient mosquito monitoring and control.

## **Features**
- **AI-Powered Mosquito Egg Counting**: Automatically detect and count mosquito eggs from ovitrap images using machine learning algorithms.
- **Hotspot Visualization**: Interactive maps to visualize mosquito breeding hotspots and trends based on ovitrap locations.
- **Real-Time Data Analysis**: Live data updates and trend analysis on mosquito populations.
- **User-Friendly Interface**: Seamless experience across web and mobile platforms (PWA) for public health officers.
- **Report Generation**: Export detailed reports in various formats (PDF, CSV) for analysis and decision-making.

## **Technologies Used**
- **Frontend**: Vue.js with Ionic for mobile and PWA support
- **Backend**: Node.js with Express.js for API development
- **AI/ML**: Python with TensorFlow or PyTorch for the AI model
- **Database**: MongoDB or PostgreSQL for data storage
- **GIS**: Leaflet.js for interactive map and hotspot visualization
- **DevOps**: Docker, CI/CD pipelines, and cloud services (AWS/GCP)

## **Project Setup**

### **Prerequisites**
- Node.js (v12 or higher)
- NPM or Yarn
- Python 3.x (for AI model development)
- MongoDB/PostgreSQL
- Docker (optional, for containerization)

### **Installation**

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/mosquieye.git
   cd mosquieye
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Set up environment variables**:
   Create a `.env` file in the root directory and add the following variables:
   ```bash
   NODE_ENV=development
   PORT=3000
   DATABASE_URL=your-database-url
   API_KEY=your-api-key
   ```

4. **Run the application**:
   ```bash
   npm run serve
   ```

5. **AI Model Setup** (Optional):
   - Navigate to the `ai` directory.
   - Install the required Python packages:
     ```bash
     pip install -r requirements.txt
     ```
   - Run the AI model for mosquito egg detection:
     ```bash
     python train_model.py
     ```

### **Development**

- **Frontend**: 
  To run the frontend (Vue.js):
  ```bash
  npm run serve
  ```

- **Backend**: 
  To run the backend (Node.js):
  ```bash
  npm run start
  ```

### **Building for Production**

To build the app for production:
```bash
npm run build
```

## **License**

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

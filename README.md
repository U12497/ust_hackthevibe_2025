# 🌐 Multi-Cloud FinOps AI System

A comprehensive Financial Operations (FinOps) management system powered by Google's Gemini 2.5 Flash AI models, designed to analyze, optimize, and provide intelligent insights across Google Cloud Platform (GCP), Amazon Web Services (AWS), and Microsoft Azure.

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Technical Architecture](#technical-architecture)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Configuration](#configuration)
- [Usage Guide](#usage-guide)
- [System Components](#system-components)
- [Data Processing](#data-processing)
- [AI Agents](#ai-agents)
- [API References](#api-references)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

## 🎯 Overview

The Multi-Cloud FinOps AI System is an enterprise-grade solution that leverages advanced AI capabilities to provide comprehensive financial operations management across multiple cloud platforms. Built with Streamlit for an intuitive web interface and powered by Google's latest Gemini 2.5 Flash models, this system offers real-time cost analysis, optimization recommendations, and intelligent query processing.

### 💡 Why This System?

- **Multi-Cloud Unified View**: Aggregate costs and insights from GCP, AWS, and Azure in one dashboard
- **AI-Powered Intelligence**: Advanced query processing with context-aware responses
- **Real-time Analytics**: Live cost monitoring and trend analysis
- **Automated Optimization**: Smart recommendations for cost reduction
- **Enterprise Ready**: Scalable architecture with robust error handling

## ✨ Key Features

### 🔄 Multi-Cloud Cost Aggregation
- **Unified Dashboard**: Combined cost view across all cloud platforms
- **Real-time Updates**: Auto-refreshing cost calculations during system initialization
- **Currency Conversion**: Automatic INR to USD conversion for standardized reporting
- **Cost Breakdown**: Detailed service-level cost analysis

### 🤖 Advanced AI Capabilities
- **Gemini 2.5 Flash Integration**: Latest Google AI models for superior performance
- **Multi-Agent Architecture**: Specialized agents for each cloud platform and general FinOps
- **Intelligent Query Routing**: Automatic detection of cloud-specific vs. generic queries
- **Context-Aware Responses**: Answers based on actual billing data and best practices

### 📊 Comprehensive Analytics
- **Interactive Visualizations**: Dynamic charts and graphs using Plotly
- **Cost Trend Analysis**: Historical spending patterns and forecasting
- **Service Usage Metrics**: Detailed breakdown by services and resources
- **Optimization Insights**: AI-driven cost reduction recommendations

### 🔧 Enhanced User Experience
- **Auto-Loading System**: Automatic data initialization on startup
- **Responsive Design**: Optimized for desktop and mobile viewing
- **Smart Sidebar**: Real-time cost display with detailed breakdowns
- **Conversational Interface**: Natural language queries with intelligent responses

## 🏗️ Technical Architecture

### System Design
```
┌─────────────────────────────────────────────────────────────┐
│                    Streamlit Frontend                       │
├─────────────────────────────────────────────────────────────┤
│                  Multi-Agent System                         │
│  ┌──────────────┬──────────────┬──────────────┬───────────┐ │
│  │   FinOps     │     GCP      │     AWS      │   Azure   │ │
│  │  RAG Agent   │ Billing Agent│ FinOps Agent │Agent      │ │
│  └──────────────┴──────────────┴──────────────┴───────────┘ │
├─────────────────────────────────────────────────────────────┤
│                    Utility Layer                            │
│  ┌──────────────┬──────────────┬──────────────┬───────────┐ │
│  │    CSV       │   Document   │Enhanced Query│Visualiza- │ │
│  │  Processor   │   Loader     │  Processor   │tion Utils │ │
│  └──────────────┴──────────────┴──────────────┴───────────┘ │
├─────────────────────────────────────────────────────────────┤
│                     Data Layer                              │
│  ┌──────────────┬──────────────┬──────────────────────────┐ │
│  │  GCP Billing │  AWS Billing │     Azure Billing        │ │
│  │    Data      │    Data      │        Data              │ │
│  └──────────────┴──────────────┴──────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

### Technology Stack
- **Frontend**: Streamlit 1.28+
- **AI/ML**: Google Vertex AI, Gemini 2.5 Flash, LangChain, LangGraph
- **Data Processing**: Pandas, NumPy, FAISS
- **Visualization**: Plotly
- **Authentication**: Google Cloud Auth
- **Environment**: Python 3.8+, Virtual Environment

## 📋 Prerequisites

### System Requirements
- **Python**: 3.8 or higher
- **Memory**: Minimum 4GB RAM (8GB recommended)
- **Storage**: At least 2GB free space
- **Network**: Internet connection for AI model access

### Cloud Platform Access
- **Google Cloud Platform**: 
  - Active GCP project with Vertex AI API enabled
  - Service account with appropriate permissions
  - Billing data export configured
- **AWS**: (Optional) Billing data export
- **Azure**: (Optional) Cost management data export

## 🚀 Installation & Setup

### 1. Clone Repository
```bash
git clone <repository-url>
cd vibe_code_hack_finops
```

### 2. Create Virtual Environment
```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# Linux/Mac
python -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Google Cloud Setup
```bash
# Install Google Cloud CLI
# https://cloud.google.com/sdk/docs/install

# Authenticate
gcloud auth login
gcloud auth application-default login

# Set project
gcloud config set project YOUR_PROJECT_ID
```

### 5. Enable Required APIs
```bash
gcloud services enable aiplatform.googleapis.com
gcloud services enable compute.googleapis.com
gcloud services enable bigquery.googleapis.com
```

## ⚙️ Configuration

### Environment Variables
Create a `.env` file in the project root:

```env
# Google Cloud Configuration
GOOGLE_CLOUD_PROJECT=your-project-id
GOOGLE_APPLICATION_CREDENTIALS=path/to/service-account-key.json

# Model Configuration
GEMINI_MODEL=gemini-2.0-flash-exp
EMBEDDING_MODEL=textembedding-gecko@003

# Application Settings
STREAMLIT_PORT=8501
DEBUG_MODE=False

# Data Paths (Optional - defaults to ./data/)
GCP_DATA_PATH=./data/gcp/
AWS_DATA_PATH=./data/aws/
AZURE_DATA_PATH=./data/azure/
```

### Data Structure
Organize your billing data in the following structure:
```
data/
├── gcp/
│   ├── billing_export.csv
│   └── service_usage.csv
├── aws/
│   ├── aws_billing.csv
│   └── cost_usage_report.csv
├── azure/
│   ├── azure_billing.csv
│   └── usage_details.csv
└── documents/
    ├── finops_best_practices.pdf
    └── cost_optimization_guide.pdf
```

### CSV Data Format Requirements

#### GCP Billing Data
```csv
service.description,sku.description,usage_start_time,usage_end_time,location.location,cost,currency
Compute Engine,N1 Predefined Instance Core running in Americas,2024-01-01,2024-01-02,us-central1-a,100.50,USD
```

#### AWS Billing Data
```csv
ServiceName,UsageType,UsageStartDate,UsageEndDate,Region,Cost,Currency
Amazon EC2,BoxUsage:t2.micro,2024-01-01,2024-01-02,us-east-1,25.30,USD
```

#### Azure Billing Data
```csv
ServiceName,MeterCategory,UsageDateTime,Location,PreTaxCost,Currency
Virtual Machines,Compute,2024-01-01T00:00:00Z,East US,45.75,USD
```

## 🎮 Usage Guide

### Starting the Application
```bash
# Activate virtual environment
.venv\Scripts\activate  # Windows
# source .venv/bin/activate  # Linux/Mac

# Run the application
streamlit run app.py

# Custom port (optional)
streamlit run app.py --server.port 8502
```

### Application Workflow

1. **System Initialization**
   - Automatic loading of all cloud billing data
   - Currency conversion and standardization
   - Cost aggregation across all platforms
   - Display of total costs in sidebar ($XX,XXX.XX format)

2. **Multi-Cloud Dashboard**
   - View aggregated costs from all cloud platforms
   - Interactive cost breakdowns and visualizations
   - Real-time updates and trend analysis

3. **AI-Powered Chat Interface**
   - Ask natural language questions about your cloud costs
   - Get intelligent, context-aware responses
   - Automatic routing to appropriate specialist agents

4. **Data Analysis & Insights**
   - Generate custom reports and visualizations
   - Identify cost optimization opportunities
   - Track spending trends and anomalies

### Example Queries

**Generic Multi-Cloud Questions:**
- "What are my top 5 most expensive services across all clouds?"
- "Show me cost trends for the last 6 months"
- "What optimization recommendations do you have?"

**Cloud-Specific Questions:**
- "What's my GCP Compute Engine spending this month?"
- "Show me AWS S3 storage costs breakdown"
- "Analyze my Azure virtual machine usage patterns"

**FinOps Best Practices:**
- "What are the latest FinOps best practices for cost optimization?"
- "How can I implement automated cost controls?"
- "What are the industry benchmarks for cloud spending?"

## 🧩 System Components

### Core Application (`app.py`)
- **Main Streamlit Interface**: Web application entry point
- **Auto-Loading System**: Automatic data initialization
- **Multi-Cloud Cost Display**: Real-time sidebar cost aggregation
- **Chat Interface**: Natural language query processing
- **Visualization Integration**: Interactive charts and metrics

### AI Agents (`agents/`)

#### FinOps RAG Agent (`finops_rag_agent.py`)
- **Purpose**: General FinOps knowledge and best practices
- **Capabilities**: Document-based Q&A, cost optimization strategies
- **Model**: Gemini 2.5 Flash with RAG (Retrieval-Augmented Generation)

#### GCP Billing Agent (`gcp_billing_agent.py`)
- **Purpose**: Google Cloud Platform billing analysis
- **Capabilities**: GCP-specific cost analysis, service optimization
- **Model**: Gemini 2.5 Flash with GCP billing data context

#### AWS FinOps Agent (`aws_finops_agent.py`)
- **Purpose**: Amazon Web Services cost management
- **Capabilities**: AWS billing analysis, service recommendations
- **Model**: Gemini 2.5 Flash with AWS billing expertise

#### Azure FinOps Agent (`azure_finops_agent.py`)
- **Purpose**: Microsoft Azure cost optimization
- **Capabilities**: Azure billing analysis, resource optimization
- **Model**: Gemini 2.5 Flash with Azure cost management focus

#### Multi-Agent System (`multi_agent_system.py`)
- **Purpose**: Orchestrates all specialist agents
- **Capabilities**: Query routing, response synthesis, multi-cloud insights
- **Features**: Enhanced query processing, intelligent agent selection

### Utility Modules (`utils/`)

#### CSV Processor (`csv_processor.py`)
- **Data Loading**: Multi-cloud CSV file processing
- **Currency Conversion**: Automatic INR to USD conversion
- **Data Standardization**: Column mapping across different cloud formats
- **Cost Aggregation**: Multi-cloud cost calculation and caching

#### Enhanced Query Processor (`enhanced_query_processor.py`)
- **Query Analysis**: Natural language understanding
- **Cloud Detection**: Automatic identification of cloud-specific queries
- **Context Enhancement**: Intelligent prompt augmentation
- **Multi-Cloud Routing**: Smart agent selection logic

#### Document Loader (`document_loader.py`)
- **PDF Processing**: FinOps document ingestion
- **Text Extraction**: Document content parsing
- **Vector Storage**: FAISS-based similarity search
- **Knowledge Base**: RAG system foundation

#### Visualization Utils (`visualizations.py`)
- **Interactive Charts**: Plotly-based cost visualizations
- **Trend Analysis**: Time-series cost plotting
- **Service Breakdown**: Pie charts and bar graphs
- **Custom Metrics**: KPI dashboards and summaries

## 📊 Data Processing

### Multi-Cloud Data Integration
The system processes billing data from multiple cloud providers with automatic standardization:

#### Data Ingestion Pipeline
1. **File Detection**: Automatic discovery of CSV files in data directories
2. **Format Recognition**: Cloud provider format identification
3. **Schema Mapping**: Column standardization across providers
4. **Currency Conversion**: Automatic INR to USD conversion for GCP data
5. **Data Validation**: Error checking and data quality assessment
6. **Aggregation**: Multi-cloud cost summation and caching

#### Supported Data Formats
- **GCP**: BigQuery billing export, detailed usage reports
- **AWS**: Cost and Usage Reports (CUR), detailed billing reports
- **Azure**: Cost Management exports, usage detail reports

#### Processing Features
- **Real-time Processing**: Live data updates during application runtime
- **Error Handling**: Robust error recovery and logging
- **Performance Optimization**: Efficient data loading with caching
- **Memory Management**: Optimized processing for large datasets

## 🤖 AI Agents

### Gemini 2.5 Flash Integration
All agents utilize Google's latest Gemini 2.5 Flash model for:
- **Enhanced Performance**: Faster response times and improved accuracy
- **Advanced Reasoning**: Complex cost analysis and optimization logic
- **Multi-modal Capabilities**: Text and data processing
- **Context Awareness**: Large context windows for comprehensive analysis

### Agent Capabilities

#### Intelligent Query Routing
- **Automatic Detection**: Identifies cloud-specific vs. generic queries
- **Context Preservation**: Maintains conversation history and context
- **Dynamic Routing**: Routes queries to appropriate specialist agents
- **Response Synthesis**: Combines insights from multiple agents

#### Cost Analysis Features
- **Trend Identification**: Automatic detection of spending patterns
- **Anomaly Detection**: Identification of unusual cost spikes
- **Optimization Recommendations**: AI-driven cost reduction strategies
- **Comparative Analysis**: Cross-cloud cost comparisons

#### Natural Language Processing
- **Query Understanding**: Advanced NLP for user intent recognition
- **Context Extraction**: Relevant information extraction from queries
- **Response Generation**: Natural, conversational AI responses
- **Multi-turn Conversations**: Context-aware dialog management

## 📚 API References

### Core Functions

#### Cost Aggregation
```python
def get_combined_cloud_costs() -> Dict[str, float]:
    """
    Retrieves and aggregates costs from all cloud platforms.
    
    Returns:
        Dict containing individual cloud costs and total
        
    Example:
        {
            'gcp': 29444.09,
            'aws': 623.53,
            'azure': 3095.07,
            'total': 33162.69
        }
    """
```

#### System Initialization
```python
def initialize_system() -> bool:
    """
    Performs enhanced system initialization with auto-loading.
    
    Returns:
        Boolean indicating successful initialization
        
    Features:
        - Automatic data loading
        - Cost calculation and display
        - Agent initialization
        - Error handling and recovery
    """
```

#### Query Processing
```python
def process_enhanced_query(query: str, context: Dict) -> Dict:
    """
    Processes user queries with enhanced multi-cloud intelligence.
    
    Args:
        query: User's natural language question
        context: Additional context and conversation history
        
    Returns:
        Dict containing response, agent used, and metadata
    """
```

### Agent APIs

#### Multi-Agent System
```python
class MultiAgentFinOpsSystem:
    def route_query(self, query: str) -> str:
        """Routes query to appropriate agent"""
        
    def synthesize_response(self, responses: List[Dict]) -> str:
        """Combines responses from multiple agents"""
        
    def get_cost_context(self) -> Dict:
        """Retrieves current cost context for responses"""
```

### Data Processing APIs

#### CSV Processor
```python
class CSVProcessor:
    def load_multi_cloud_data(self) -> Dict[str, pd.DataFrame]:
        """Loads and processes all cloud billing data"""
        
    def convert_currency(self, amount: float, from_currency: str, to_currency: str) -> float:
        """Converts currency amounts"""
        
    def standardize_columns(self, df: pd.DataFrame, cloud_type: str) -> pd.DataFrame:
        """Standardizes column names across cloud providers"""
```

## 🔧 Troubleshooting

### Common Issues

#### Authentication Problems
**Issue**: Google Cloud authentication failures
```bash
# Solution: Re-authenticate
gcloud auth login
gcloud auth application-default login
```

#### Missing Dependencies
**Issue**: Import errors or missing packages
```bash
# Solution: Reinstall dependencies
pip install -r requirements.txt --upgrade
```

#### Data Loading Errors
**Issue**: CSV files not loading properly
- **Check Data Format**: Ensure CSV files match expected schema
- **Verify File Paths**: Confirm data files are in correct directories
- **Check Permissions**: Ensure read access to data files

#### Memory Issues
**Issue**: Out of memory errors with large datasets
- **Reduce Data Size**: Process data in smaller chunks
- **Increase System Memory**: Add more RAM or use cloud instances
- **Optimize Processing**: Enable data streaming and caching

### Performance Optimization

#### Application Performance
- **Enable Caching**: Use Streamlit caching for data processing
- **Optimize Queries**: Reduce unnecessary API calls
- **Memory Management**: Clear unused data and variables

#### AI Model Performance
- **Context Optimization**: Provide relevant context without overwhelming models
- **Query Optimization**: Structure queries for better AI understanding
- **Response Caching**: Cache common query responses

### Debugging Tips

#### Enable Debug Mode
```env
DEBUG_MODE=True
```

#### Check Logs
- **Streamlit Logs**: Check console output for errors
- **Application Logs**: Monitor custom logging output
- **Google Cloud Logs**: Check Vertex AI API call logs

#### Data Validation
```python
# Validate data loading
def validate_data():
    processor = CSVProcessor()
    data = processor.load_multi_cloud_data()
    for cloud, df in data.items():
        print(f"{cloud}: {len(df)} rows loaded")
```

## 🤝 Contributing

### Development Setup
1. Fork the repository
2. Create a feature branch
3. Set up development environment
4. Install pre-commit hooks
5. Make changes and test thoroughly
6. Submit pull request

### Code Standards
- **Python Style**: Follow PEP 8 guidelines
- **Documentation**: Add docstrings for all functions
- **Testing**: Include unit tests for new features
- **Type Hints**: Use type annotations where applicable

### Feature Requests
- **Issue Templates**: Use provided issue templates
- **Feature Proposals**: Include detailed use cases
- **Technical Specifications**: Provide implementation details

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- **Google Cloud Team**: For Vertex AI and Gemini model access
- **Streamlit Community**: For the excellent web framework
- **LangChain Team**: For AI orchestration capabilities
- **Open Source Contributors**: For the various libraries used

## 📞 Support

For technical support and questions:
- **Documentation**: Check this README and inline code documentation
- **Issues**: Create GitHub issues for bug reports
- **Discussions**: Use GitHub discussions for feature requests
- **Community**: Join our community forums

---

**Version**: 2.5.0  
**Last Updated**: September 2025  
**Compatibility**: Python 3.8+, Streamlit 1.28+, Gemini 2.5 Flash

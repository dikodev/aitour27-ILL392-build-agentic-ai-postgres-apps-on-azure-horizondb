# Lab Setup

If you are trying this lab at home, make sure to complete all these steps before starting the lab exercises.

## Prerequisites

- An **Azure subscription** with access to **Azure OpenAI** and **Azure HorizonDB**.
- **Visual Studio Code** with the **Jupyter** and **PostgreSQL** extensions installed.
- A **Python 3.11+** environment with the packages listed in [`/requirements.txt`](/requirements.txt):
  - Database connectivity: `psycopg[binary,pool]`
  - LLM and agent framework: `openai`, `agent-framework`
  - Long-term memory: `mem0`
  - Notebook compatibility: `jupyter`, `ipywidgets`, `nest_asyncio`
  - Data validation: `pydantic`
  - HTTP: `requests`
  - Environment management: `python-dotenv`
  - UI: `gradio`


## Setup your python environment and install dependencies

Complete the following steps inside the root directory of the repository.

1. Create a virtual environment:
    - Windows (PowerShell): `python -m venv .venv`
    - macOS/Linux: `python3 -m venv .venv`

1. Activate the virtual environment:
    - Windows (PowerShell): `.\.venv\Scripts\Activate.ps1`
    - macOS/Linux: `source .venv/bin/activate`

1. Upgrade pip:

    ```powershell
    python -m pip install --upgrade pip
    ```

1. Install the required packages:

    ```powershell
    python -m pip install -r requirements.txt
    ```

1. In Visual Studio Code, select the `.venv` interpreter for your notebooks (Command Palette -> **Python: Select Interpreter**).

1. Verify the installation by running `python -m pip list` to ensure all required packages are installed.

## Deploy HorizonDB and Azure OpenAI resources

1. Install the Azure CLI if you haven't already: [Install Azure CLI](https://learn.microsoft.com/cli/azure/install-azure-cli)

1. Sign in to your Azure account:

    ```powershell
    az auth login
    ```

1. Initialize an environment name

    ```powershell
    azd env new <environment-name>
    ```

1. Provision the infrastructure and run post-provision hooks:

    ```powershell
    azd up
    ```

1. After the provisioning is complete, your repo root `.env` is created and updated with the environment configuration and is ready for the notebooks.

> [!IMPORTANT]
> **Allow your IP on HorizonDB**. The post-provision hook does not configure HorizonDB networking. Before you can connect from your machine, open the deployed HorizonDB cluster in the Azure portal, go to **Settings > Networking**, and add a firewall rule that allow-lists your current public IP address. Without this step, notebook connections will fail with a network/timeout error.

You can now proceed and start working on the first exercise in the lab. Navigate to the [`instructions/`](/instructions/) folder.

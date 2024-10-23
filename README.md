
---

# Rule Engine with AST  
**Zeotap | Software Engineer Intern | Assignment**

## Applicant Introduction  
Hi, I'm **Nallapareddy Siri**, a B.E. Computer Science student and tech enthusiast. I enjoy developing projects using modern frameworks and learning new technologies. Currently, I'm involved in projects that include a **Real-Time Weather Monitoring System** and **Seat Booking Systems**, and I'm constantly pushing my limits in AI and full-stack development.

## Table of Contents  
- [Introduction](#introduction)  
- [Technical Parts](#technical-parts)  
  - [Installation](#installation)  
  - [How to run](#how-to-run)  
  - [About Solution](#about-solution)  
  - [Solution Overview](#solution-overview)  
  - [Code Structure](#code-structure)  
- [Non-Technical Parts](#non-technical-parts)  
  - [My Approach](#my-approach)  
  - [Feedback](#feedback)  
  - [Outro](#outro)

---

## Introduction  
The following README is organized into technical and non-technical sections. The technical parts focus on the solution, code structure, and setup, while the non-technical parts dive into my thought process and approach to the project. The **AST (Abstract Syntax Tree)** based rule engine is designed to process and evaluate rules dynamically, allowing flexible rule modification.

---

## Technical Parts  

### Installation  
The project has been designed to be cross-platform and packaged in a Docker container for ease of setup. Alternatively, you can run the components manually by following these steps.

#### Frontend  
```
cd frontend/
npm install
```

#### Backend  
Make sure Poetry is installed before proceeding. If not, install it as follows:  
```bash
python3 -m venv $VENV_PATH  
$VENV_PATH/bin/pip install -U pip setuptools  
$VENV_PATH/bin/pip install poetry  
```

Then, create a virtual environment and install the necessary dependencies:  
```bash
cd backend/
poetry install
```

#### Database  
Set up the Postgres database by running:  
```bash
docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d postgres
```

Ensure you populate your `.env` file with the necessary database credentials.

---

### How to Run  
Assuming the installation steps were completed successfully:

#### Frontend  
```bash
npm run dev
```

#### Backend  
```bash
poetry run python main.py --dev
```

#### Database  
```bash
docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d postgres
```

---

### About Solution  
This project consists of three major components:  
- **UI** using **Next.js** to visualize the AST.  
- **API** built with **FastAPI** for rule parsing and processing.  
- **PostgreSQL database** for persistent storage of AST nodes.

### Solution Overview  
- The **UI** sends HTTP requests to the REST API and visualizes the AST with **React-D3-Tree**.  
- The **backend** tokenizes input rules using a `tokenizer()` and parses them into an AST structure using a `Parser`.  
- The AST is serialized into **JSON** for storage in the database. A more advanced approach could use hashing and pointers for efficient storage, optimizing for space while maintaining data isolation.  
- The rule engine can dynamically process, evaluate, and combine rules based on logical operators (e.g., AND, OR).

---

### Code Structure  
The project is organized into distinct directories for frontend and backend, with each file serving a clear purpose.

#### Backend  
| File | Description |  
| --- | --- |  
| `main.py` | Entrypoint of the server |  
| `poetry.lock` | Poetry-managed dependencies |  
| `pyproject.toml` | Project metadata |  
| `rule_engine/ast_utils.py` | AST class definitions and utilities |  
| `rule_engine/database.py` | ORM and database operations |  
| `rule_engine/main.py` | API endpoints and contracts |  
| `rule_engine/models.py` | Database schema definitions |  
| `rule_engine/parser_utils.py` | Tokenizer and Parser functions |  

#### Frontend  
| File | Description |  
| --- | --- |  
| `app/` | Source code for the application |  
| `app/components/ASTTree.tsx` | Component to render AST visualization |  
| `app/services/api.ts` | Middleware to connect to the backend API |  
| `app/page.tsx` | Main UI page |  

---

## Non-Technical Parts  

### My Approach  
1. **Deep understanding**: My first step was thoroughly reading the assignment and ensuring I had a full grasp of the requirements.  
2. **Literature Review**: I researched **frequent operator heuristics** to ensure I implemented the best approach for rule combination.  
3. **Compiler analogy**: Having worked on compilers with **lex and bison**, I applied similar strategies here for parsing and AST creation.  
4. **AST design**: I designed the core classes like `Node`, `Operator`, and `Condition`, ensuring each component was well-structured and flexible.  
5. **Parser Implementation**: The tokenizer and parser were built to break down input strings and generate corresponding ASTs.  
6. **Tree Traversal**: The algorithm for traversing the AST supports dynamic rule creation, condition evaluation, and efficient storage.

---

### Feedback  
This assignment was both challenging and enjoyable. It required blending academic knowledge with practical implementation, pushing me to use skills from compiler design, data structures, and system architecture. It was a valuable learning experience!

---

### Outro  
Thank you for reviewing this project. I hope this README and the code repository give you a clear understanding of the solution and its design. I look forward to any feedback or suggestions!

---

This format is ready to be used on GitHub, and it provides both a technical and a non-technical view of the solution, making it easier for anyone to understand your approach. Let me know if you need any further adjustments!

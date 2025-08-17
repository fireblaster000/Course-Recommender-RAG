<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LUMS Course Assistant - RAG Model</title>
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --success: #2ecc71;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f9f9f9;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 2rem;
            border-radius: 8px;
            margin-bottom: 2rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        
        h1 {
            margin: 0;
            font-size: 2.5rem;
        }
        
        h2 {
            color: var(--primary);
            border-bottom: 2px solid var(--secondary);
            padding-bottom: 0.5rem;
            margin-top: 2rem;
        }
        
        h3 {
            color: var(--secondary);
        }
        
        .team-members {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            justify-content: center;
            margin: 1.5rem 0;
        }
        
        .member {
            background-color: white;
            padding: 1rem;
            border-radius: 6px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            flex: 1 1 200px;
            max-width: 300px;
        }
        
        .badge {
            display: inline-block;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            font-size: 0.8rem;
            font-weight: bold;
            margin-right: 0.5rem;
            margin-bottom: 0.5rem;
        }
        
        .tech-badge {
            background-color: var(--secondary);
            color: white;
        }
        
        .feature-badge {
            background-color: var(--success);
            color: white;
        }
        
        .section {
            background-color: white;
            padding: 1.5rem;
            border-radius: 8px;
            margin-bottom: 2rem;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.5rem;
        }
        
        .feature {
            background-color: #f8f9fa;
            padding: 1.5rem;
            border-radius: 8px;
            border-left: 4px solid var(--secondary);
        }
        
        .tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
        }
        
        .tech-item {
            background-color: var(--light);
            padding: 1rem;
            border-radius: 6px;
            flex: 1 1 200px;
            text-align: center;
        }
        
        .tech-item img {
            height: 50px;
            margin-bottom: 0.5rem;
        }
        
        .cta {
            text-align: center;
            padding: 2rem;
            background: linear-gradient(135deg, var(--secondary), var(--primary));
            color: white;
            border-radius: 8px;
            margin-top: 2rem;
        }
        
        .btn {
            display: inline-block;
            padding: 0.8rem 1.5rem;
            background-color: var(--accent);
            color: white;
            text-decoration: none;
            border-radius: 4px;
            font-weight: bold;
            margin-top: 1rem;
            transition: transform 0.2s, box-shadow 0.2s;
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        
        footer {
            text-align: center;
            margin-top: 3rem;
            padding: 1rem;
            color: #777;
        }
    </style>
</head>
<body>
    <header>
        <h1>LUMS Course Assistant</h1>
        <p>A Retrieval-Augmented Generation (RAG) model for academic course selection assistance at LUMS</p>
    </header>
    
    <div class="section">
        <h2>Project Overview</h2>
        <p>The LUMS Course Assistant is an advanced AI system designed to help students at Lahore University of Management Sciences (LUMS) make informed course selection decisions. By leveraging Retrieval-Augmented Generation (RAG) architecture, the system provides personalized recommendations based on historical course reviews and official course outlines.</p>
        
        <p>Our model integrates cutting-edge natural language processing techniques with a user-friendly interface to deliver accurate, context-aware advice about courses, professors, workload, and more.</p>
    </div>
    
    <div class="section">
        <h2>Key Features</h2>
        <div class="features">
            <div class="feature">
                <h3>Course Recommendations</h3>
                <p>Get personalized course suggestions based on your academic level, interests, and past reviews from students with similar profiles.</p>
            </div>
            
            <div class="feature">
                <h3>Detailed Reviews</h3>
                <p>Access comprehensive reviews from previous students about course difficulty, workload, grading, and teaching quality.</p>
            </div>
            
            <div class="feature">
                <h3>Semester Planning</h3>
                <p>Discover which courses are typically offered in specific semesters and plan your academic journey accordingly.</p>
            </div>
            
            <div class="feature">
                <h3>Conversational Interface</h3>
                <p>Interact with our AI assistant through natural language queries, just like chatting with an experienced peer.</p>
            </div>
            
            <div class="feature">
                <h3>Course Outlines</h3>
                <p>Access official course outlines with component breakdowns, prerequisites, and study resources.</p>
            </div>
            
            <div class="feature">
                <h3>Context-Aware Responses</h3>
                <p>The system maintains conversation context for follow-up questions and personalized advice.</p>
            </div>
        </div>
    </div>
    
    <div class="section">
        <h2>Technical Implementation</h2>
        
        <h3>Data Collection</h3>
        <p>Our dataset consists of:</p>
        <ul>
            <li><strong>471 student reviews</strong> collected through Google Forms and manually scraped from the LUMS Discussion Forum (LDF)</li>
            <li><strong>170 course outlines</strong> downloaded from the LUMS Registrar Portal</li>
            <li>Manually annotated metadata including course abbreviations, aliases, and offering semesters</li>
        </ul>
        
        <h3>Technology Stack</h3>
        <div class="tech-stack">
            <div class="tech-item">
                <h4>Embeddings</h4>
                <p>OllamaEmbeddings with nomic-embed-text model</p>
                <span class="badge tech-badge">State-of-the-art retrieval</span>
                <span class="badge tech-badge">Memory efficient</span>
            </div>
            
            <div class="tech-item">
                <h4>Vector Database</h4>
                <p>Chroma DB</p>
                <span class="badge tech-badge">Open source</span>
                <span class="badge tech-badge">High performance</span>
            </div>
            
            <div class="tech-item">
                <h4>LLM</h4>
                <p>Mistral-7B-Instruct-v0.2</p>
                <span class="badge tech-badge">7B parameters</span>
                <span class="badge tech-badge">Instruct fine-tuned</span>
            </div>
            
            <div class="tech-item">
                <h4>Framework</h4>
                <p>LangChain</p>
                <span class="badge tech-badge">Modular design</span>
                <span class="badge tech-badge">RAG optimized</span>
            </div>
            
            <div class="tech-item">
                <h4>Interface</h4>
                <p>Gradio + ngrok</p>
                <span class="badge tech-badge">User-friendly</span>
                <span class="badge tech-badge">Web accessible</span>
            </div>
        </div>
        
        <h3>System Architecture</h3>
        <p>The RAG pipeline consists of:</p>
        <ol>
            <li><strong>Document Loading:</strong> Using Docx2txtLoader for text documents and PyPDFLoader for course outlines</li>
            <li><strong>Vector Storage:</strong> Chroma DB with nomic-embed-text embeddings for semantic search</li>
            <li><strong>Retrieval:</strong> Similarity-based document retrieval with carefully tuned parameters</li>
            <li><strong>Generation:</strong> Mistral-7B-Instruct model with custom prompt engineering</li>
            <li><strong>Memory:</strong> ConversationBufferMemory to maintain context (K=3 interactions)</li>
        </ol>
    </div>
    
    <div class="section">
        <h2>Development Team</h2>
        <div class="team-members">
            <div class="member">
                <h4>Mustafa Abbas</h4>
                <p>25100079</p>
                <ul>
                    <li>Project documentation lead</li>
                    <li>LLM research</li>
                    <li>Pipeline architecture</li>
                </ul>
            </div>
            
            <div class="member">
                <h4>Raahem Nabeel</h4>
                <p>25100079</p>
                <ul>
                    <li>Pipeline architecture</li>
                    <li>Debugging</li>
                    <li>UI development</li>
                </ul>
            </div>
            
            <div class="member">
                <h4>Ibrahim Farrukh</h4>
                <p>25100227</p>
                <ul>
                    <li>Data collection lead</li>
                    <li>Course outline extraction</li>
                    <li>Pipeline architecture</li>
                </ul>
            </div>
            
            <div class="member">
                <h4>Jawad Saeed</h4>
                <p>25100094</p>
                <ul>
                    <li>Vector embeddings</li>
                    <li>LLM experimentation</li>
                    <li>Pipeline architecture</li>
                </ul>
            </div>
            
            <div class="member">
                <h4>Safiullah Sarfaraz</h4>
                <p>25100227</p>
                <ul>
                    <li>Data collection</li>
                    <li>EDA</li>
                    <li>Data annotation</li>
                </ul>
            </div>
        </div>
    </div>
    
    <footer>
        <p>© 2024 LUMS Course Assistant Team</p>
    </footer>
</body>
</html>

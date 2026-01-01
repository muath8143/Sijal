<h1>Sijal (سِجال) – AI-Powered Interview Preparation Platform</h1>

<p>
<strong>Sijal (سِجال)</strong> is an AI-powered interview preparation platform designed to help job seekers
experience realistic interview simulations and receive actionable, structured feedback.
The platform combines artificial intelligence with human HR evaluation to deliver
a comprehensive and practical interview readiness experience.
</p>

<p>
Users can initiate interview sessions based on their CV or a specific job description,
participate in voice-based interview simulations, and receive detailed performance evaluations
including strengths, weaknesses, final scores, and personalized improvement plans.
</p>

<p>
سِجال هي منصة ذكية للاستعداد للمقابلات الوظيفية، تهدف إلى محاكاة بيئة المقابلات الواقعية
وتحليل أداء المتقدم بشكل عملي ودقيق.
تعتمد المنصة على الذكاء الاصطناعي إلى جانب التقييم الاحترافي من مختصي الموارد البشرية
لتقديم تجربة شاملة تعكس متطلبات سوق العمل الحقيقي.
</p>

<p>
تمكّن المنصة المستخدم من إنشاء جلسة مقابلة بناءً على سيرته الذاتية أو الوصف الوظيفي،
الدخول في مقابلة صوتية تفاعلية، ثم الحصول على تقرير تفصيلي يشمل التقييم النهائي،
نقاط القوة، نقاط الضعف، وخطة تطوير شخصية مدعومة بالذكاء الاصطناعي.
</p>

<hr/>

<h2>Key Features</h2>
<ul>
  <li>AI-generated interview sessions based on CV or job description</li>
  <li>Voice-based interview simulation using AI agents</li>
  <li>Automated interview analysis with scoring and detailed feedback</li>
  <li>HR-led interview evaluation and professional assessment</li>
  <li>AI-generated personalized improvement and development plans</li>
  <li>Secure authentication and authorization using JWT</li>
  <li>Email notifications for interview session details</li>
</ul>

<hr/>

<h2>System Workflow</h2>
<ol>
  <li>User creates an interview session using CV or job description</li>
  <li>Interview questions are generated dynamically</li>
  <li>User joins a voice interview by calling the provided number</li>
  <li>Interview is recorded and transcribed automatically</li>
  <li>AI analyzes the interview and generates structured feedback</li>
  <li>HR evaluation and scoring are added when applicable</li>
  <li>User receives a detailed analysis and improvement plan</li>
</ol>

<hr/>

<h2>Tech Stack</h2>
<table border="1" cellpadding="8">
  <tr><th>Area</th><th>Technology</th></tr>
  <tr><td>Backend</td><td>Spring Boot, Spring MVC, Spring Data JPA</td></tr>
  <tr><td>Security</td><td>Spring Security, JWT, BCrypt</td></tr>
  <tr><td>Database</td><td>MySQL (AWS RDS)</td></tr>
  <tr><td>AI Integration</td><td>OpenAI API</td></tr>
  <tr><td>Voice Interviews</td><td>Vapi AI</td></tr>
  <tr><td>Email Service</td><td>Spring Boot Mail (SMTP)</td></tr>
  <tr><td>Deployment</td><td>AWS Elastic Beanstalk, EC2</td></tr>
</table>

<hr/>
<hr/>

<h2>Core Domain Models & Services</h2>

<p>
The following components represent the core backend logic responsible for managing
interview sessions, questions, AI analysis, and voice interview processing.
These components handle the interview lifecycle from session creation to final evaluation
and feedback delivery.
</p>

<h3>Domain Models</h3>
<ul>
  <li>
    <strong>InterviewSession</strong><br/>
    Represents an interview session created by the user, including its status,
    creation time, associated questions, and related analysis and recordings.
  </li>

  <li>
    <strong>Question</strong><br/>
    Stores dynamically generated interview questions linked to a specific interview session.
  </li>

  <li>
    <strong>InterviewAnalysisByAi</strong><br/>
    Holds AI-generated interview evaluation results such as final score,
    strengths, and weaknesses for a completed session.
  </li>

  <li>
    <strong>RecordingInterview</strong><br/>
    Manages voice interview recordings and transcripts received from the voice AI provider.
  </li>
</ul>

<h3>Application Services</h3>
<ul>
  <li>
    <strong>InterviewSessionService</strong><br/>
    Handles interview session creation, validation, question generation,
    subscription checks, and secure session access.
  </li>

  <li>
    <strong>QuestionService</strong><br/>
    Responsible for generating interview questions using AI based on the user’s CV
    and optional job description, and retrieving session-related questions.
  </li>

  <li>
    <strong>InterviewAnalysisByAiService</strong><br/>
    Processes interview transcripts, interacts with the AI engine,
    generates structured analysis results, and persists evaluation data.
  </li>

  <li>
    <strong>RecordingInterviewService</strong><br/>
    Handles incoming webhooks from the voice interview provider,
    extracts session identifiers, stores recordings, transcripts,
    and triggers AI analysis upon interview completion.
  </li>

  <li>
    <strong>OpenAiService</strong><br/>
    Manages all interactions with the OpenAI API,
    including prompt construction, response parsing,
    and structured JSON output handling.
  </li>
</ul>
<h2>API Endpoints Overview</h2>
<table border="1" cellpadding="8">
  <tr>
    <th>#</th><th>Method</th><th>Endpoint</th><th>Description</th>
  </tr>

  <tr><td>1</td><td>GET</td><td>/health</td><td>Application health check</td></tr>

  <tr><td>2</td><td>POST</td><td>/api/v1/interview-session/start-session-with-cv</td><td>Start interview using CV</td></tr>
  <tr><td>3</td><td>POST</td><td>/api/v1/interview-session/start-session-with-description</td><td>Start interview using job description</td></tr>
  <tr><td>4</td><td>GET</td><td>/api/v1/interview-session/get-my-sessions</td><td>Retrieve user interview sessions</td></tr>
  <tr><td>5</td><td>GET</td><td>/api/v1/interview-session/get-session-by-id/{id}</td><td>Retrieve session details</td></tr>
  <tr><td>6</td><td>GET</td><td>/api/v1/interview-session/get_question/{sessionId}</td><td>Retrieve session questions</td></tr>

  <tr><td>7</td><td>GET</td><td>/api/v1/analysis-by-ai/all-analysis</td><td>Retrieve all AI analyses</td></tr>
  <tr><td>8</td><td>GET</td><td>/api/v1/analysis-by-ai/analysis-for-session/{sessionId}</td><td>Retrieve analysis for a specific session</td></tr>

  <tr><td>9</td><td>GET</td><td>/api/v1/questions/questions-for-session/{sessionId}</td><td>Retrieve interview questions</td></tr>

  <tr><td>10</td><td>POST</td><td>/api/v1/vapi/webhook</td><td>Handle voice interview webhook</td></tr>
</table>

<hr/>

<h2>Deployment</h2>
<p>
The backend application is deployed on AWS using a scalable and production-ready setup.
AWS Elastic Beanstalk is used for application hosting, with EC2 handling compute resources
and RDS (MySQL) managing persistent data storage.
</p>

<p>
The system includes health checks and monitoring to ensure application availability
and stability in production.
</p>

<hr/>
<img width="1675" height="1680" alt="Blank diagram" src="https://github.com/user-attachments/assets/b62ea710-da1c-4719-a176-cb5e87826716" />

<h2>Project Resources</h2>
<ul>
  <li>ERD Diagram: <a href="#">https://lucid.app/lucidchart/ed586add-f401-4cce-8977-6620e5f93367/edit?invitationId=inv_c1f6603d-7adb-4735-a2e4-e164ef1abef8&page=0_0#</a></li>
  <li>Postman Documentation: <a href="#">https://documenter.getpostman.com/view/51095397/2sBXVbJZNn</a></li>
  <li>Figma Design: <a href="#">https://www.figma.com/design/NIJsffp2YQOJp0cQm8bale/final-project?node-id=0-1&t=wBFLfeHHZzeEQ0Hg-1</a></li>
  <li>Production Domain: <a href="https://sijal.tech">https://sijal.tech</a></li>
</ul>

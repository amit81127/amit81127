import React, { useState, useEffect } from 'react';
import { Code, Palette, Zap, Github, Linkedin, Mail, Menu, X, ExternalLink, Trophy, Target, Rocket, Brain, Car, ShoppingBag, User } from 'lucide-react';

export default function InteractivePortfolio() {
  const [activeSection, setActiveSection] = useState('about');
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });
  const [menuOpen, setMenuOpen] = useState(false);
  const [skillsHover, setSkillsHover] = useState(null);
  const [typingText, setTypingText] = useState('');
  const [typingIndex, setTypingIndex] = useState(0);

  const typingPhrases = [
    'Full Stack Web Developer',
    'MERN Stack | Java | DSA',
    'Building Scalable Web Apps',
    'Exploring AI and Automation',
    'Always Learning New Tech!'
  ];

  useEffect(() => {
    const handleMouseMove = (e) => {
      setMousePosition({ x: e.clientX, y: e.clientY });
    };
    window.addEventListener('mousemove', handleMouseMove);
    return () => window.removeEventListener('mousemove', handleMouseMove);
  }, []);

  useEffect(() => {
    const currentPhrase = typingPhrases[typingIndex];
    if (typingText.length < currentPhrase.length) {
      setTimeout(() => {
        setTypingText(currentPhrase.slice(0, typingText.length + 1));
      }, 100);
    } else {
      setTimeout(() => {
        setTypingText('');
        setTypingIndex((typingIndex + 1) % typingPhrases.length);
      }, 2000);
    }
  }, [typingText, typingIndex]);

  const skills = [
    { name: 'HTML5', color: 'from-orange-500 to-red-500', icon: '🌐', level: 90 },
    { name: 'CSS3', color: 'from-blue-500 to-cyan-500', icon: '🎨', level: 85 },
    { name: 'JavaScript', color: 'from-yellow-400 to-yellow-600', icon: '⚡', level: 88 },
    { name: 'Node.js', color: 'from-green-500 to-green-700', icon: '🟢', level: 82 },
    { name: 'Express.js', color: 'from-gray-600 to-gray-800', icon: '🚀', level: 80 },
    { name: 'MongoDB', color: 'from-green-600 to-green-800', icon: '🍃', level: 78 },
    { name: 'C', color: 'from-blue-600 to-blue-800', icon: '⚙️', level: 75 },
    { name: 'Java', color: 'from-red-600 to-orange-600', icon: '☕', level: 80 },
    { name: 'Git & GitHub', color: 'from-orange-500 to-red-600', icon: '📦', level: 85 },
    { name: 'Tailwind CSS', color: 'from-cyan-400 to-blue-500', icon: '💨', level: 83 }
  ];

  const tools = [
    { name: 'VS Code', icon: '💻' },
    { name: 'Postman', icon: '📮' },
    { name: 'Git & GitHub', icon: '🔧' },
    { name: 'MongoDB Compass', icon: '🧭' },
    { name: 'Figma', icon: '🎨' }
  ];

  const interests = [
    { icon: <Code className="w-6 h-6" />, title: 'Web Development', desc: 'Responsive & scalable web apps' },
    { icon: <Palette className="w-6 h-6" />, title: 'UI/UX Design', desc: 'Modern UI with CSS & Tailwind' },
    { icon: <Zap className="w-6 h-6" />, title: 'API Development', desc: 'Building APIs with Node.js & Express' },
    { icon: <Brain className="w-6 h-6" />, title: 'AI & Automation', desc: 'Experimenting with AI agents' },
    { icon: <Code className="w-6 h-6" />, title: 'DSA in Java', desc: 'Strong programming foundations' },
    { icon: <Rocket className="w-6 h-6" />, title: 'Database Design', desc: 'MongoDB schema architecture' }
  ];

  const projects = [
    { 
      name: 'HackChat', 
      tech: 'Next.js, AI', 
      desc: 'AI-powered chat application',
      color: 'bg-gradient-to-br from-purple-500 to-pink-500',
      icon: <Brain className="w-8 h-8" />
    },
    { 
      name: 'Smart Parking System', 
      tech: 'IoT, Arduino', 
      desc: 'RFID + Servo based automation',
      color: 'bg-gradient-to-br from-blue-500 to-cyan-500',
      icon: <Car className="w-8 h-8" />
    },
    { 
      name: 'Portfolio Website', 
      tech: 'Next.js, Tailwind', 
      desc: 'Personal branding platform',
      color: 'bg-gradient-to-br from-orange-500 to-red-500',
      icon: <User className="w-8 h-8" />
    },
    { 
      name: 'RetailMate', 
      tech: 'AI, Voice Bot', 
      desc: 'Smart retail assistant',
      color: 'bg-gradient-to-br from-green-500 to-emerald-500',
      icon: <ShoppingBag className="w-8 h-8" />
    }
  ];

  const careerGoals = [
    { goal: 'DSA in Java', progress: 70 },
    { goal: 'System Design Basics', progress: 50 },
    { goal: 'Full Stack Development', progress: 85 },
    { goal: 'Real-world Projects', progress: 75 }
  ];

  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-900 via-purple-900 to-gray-900 text-white overflow-hidden relative">
      {/* Animated background gradient */}
      <div 
        className="absolute inset-0 opacity-30 pointer-events-none transition-all duration-300"
        style={{
          background: `radial-gradient(circle 800px at ${mousePosition.x}px ${mousePosition.y}px, rgba(147, 51, 234, 0.3), transparent)`
        }}
      />

      {/* Floating particles */}
      <div className="absolute inset-0 overflow-hidden pointer-events-none">
        {[...Array(20)].map((_, i) => (
          <div
            key={i}
            className="absolute w-2 h-2 bg-purple-500 rounded-full opacity-20 animate-float"
            style={{
              left: `${Math.random() * 100}%`,
              top: `${Math.random() * 100}%`,
              animationDelay: `${Math.random() * 5}s`,
              animationDuration: `${5 + Math.random() * 10}s`
            }}
          />
        ))}
      </div>

      {/* Navigation */}
      <nav className="relative z-50 px-6 py-4 flex justify-between items-center backdrop-blur-sm bg-white/5 border-b border-purple-500/20">
        <div className="text-2xl font-bold bg-gradient-to-r from-cyan-400 to-purple-500 bg-clip-text text-transparent">
          AKP.dev
        </div>
        
        {/* Desktop Menu */}
        <div className="hidden md:flex gap-4">
          {['About', 'Skills', 'Projects', 'Goals', 'Contact'].map((item) => (
            <button
              key={item}
              onClick={() => setActiveSection(item.toLowerCase())}
              className={`px-4 py-2 rounded-lg transition-all ${
                activeSection === item.toLowerCase()
                  ? 'bg-gradient-to-r from-purple-600 to-pink-600 shadow-lg shadow-purple-500/50'
                  : 'hover:bg-white/10'
              }`}
            >
              {item}
            </button>
          ))}
        </div>

        {/* Mobile Menu Button */}
        <button 
          className="md:hidden"
          onClick={() => setMenuOpen(!menuOpen)}
        >
          {menuOpen ? <X /> : <Menu />}
        </button>
      </nav>

      {/* Mobile Menu */}
      {menuOpen && (
        <div className="md:hidden absolute top-16 left-0 right-0 bg-gray-900/95 backdrop-blur-lg z-40 p-6 space-y-4 border-b border-purple-500/20">
          {['About', 'Skills', 'Projects', 'Goals', 'Contact'].map((item) => (
            <button
              key={item}
              onClick={() => {
                setActiveSection(item.toLowerCase());
                setMenuOpen(false);
              }}
              className="block w-full text-left px-4 py-3 rounded-lg hover:bg-purple-600 transition-all"
            >
              {item}
            </button>
          ))}
        </div>
      )}

      {/* Main Content */}
      <main className="relative z-10 container mx-auto px-6 py-12">
        {/* Hero Section */}
        {activeSection === 'about' && (
          <div className="animate-fadeIn">
            <div className="max-w-4xl mx-auto text-center mb-16">
              <div className="mb-8 inline-block">
                <div className="w-32 h-32 rounded-full bg-gradient-to-br from-cyan-500 via-purple-500 to-pink-500 flex items-center justify-center text-5xl shadow-2xl shadow-purple-500/50 animate-pulse-slow">
                  👨‍💻
                </div>
              </div>
              <h1 className="text-5xl md:text-7xl font-bold mb-4">
                Hi 👋, I'm <span className="bg-gradient-to-r from-cyan-400 via-purple-500 to-pink-500 bg-clip-text text-transparent">Amit Kumar Prasad</span>
              </h1>
              <p className="text-xl md:text-2xl text-purple-300 mb-4">
                🚀 Web Developer | MERN Enthusiast | AI Explorer
              </p>
              <div className="h-8 mb-8">
                <p className="text-cyan-400 text-lg font-mono">
                  {typingText}<span className="animate-blink">|</span>
                </p>
              </div>
              
              <div className="bg-white/5 backdrop-blur-sm border border-purple-500/20 rounded-2xl p-6 mb-8 max-w-2xl mx-auto">
                <p className="text-gray-300 text-lg mb-4">
                  🎓 <strong>B.Tech CSE Student</strong> | Axis College
                </p>
                <p className="text-gray-300 text-lg mb-4">
                  📍 Kanpur, India
                </p>
                <p className="text-gray-300 text-lg mb-4">
                  I am a passionate <strong className="text-purple-400">Full Stack Web Developer</strong> with strong interest in <strong className="text-cyan-400">MERN Stack, UI/UX Design, and AI-powered applications</strong>.
                </p>
                <p className="text-gray-300 text-lg">
                  I love transforming ideas into real-world products and writing clean, maintainable code.
                </p>
              </div>

              <div className="bg-gradient-to-r from-purple-600/20 to-pink-600/20 border border-purple-500/30 rounded-2xl p-6 mb-8 max-w-2xl mx-auto">
                <p className="text-cyan-400 text-lg italic">
                  "Code is not just syntax, it's problem-solving made executable."
                </p>
              </div>

              <div className="flex gap-4 justify-center mb-12">
                <a href="https://linkedin.com/in/amit-kumar-prasad-55a070275/" target="_blank" rel="noopener noreferrer"
                   className="flex items-center gap-2 px-6 py-3 bg-blue-600 hover:bg-blue-700 rounded-full transition-all hover:scale-105 shadow-lg">
                  <Linkedin className="w-5 h-5" /> LinkedIn
                </a>
                <a href="https://github.com/amit81127" target="_blank" rel="noopener noreferrer"
                   className="flex items-center gap-2 px-6 py-3 bg-gray-800 hover:bg-gray-700 rounded-full transition-all hover:scale-105 shadow-lg">
                  <Github className="w-5 h-5" /> GitHub
                </a>
                <a href="mailto:h2307190100015@gmail.com"
                   className="flex items-center gap-2 px-6 py-3 bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 rounded-full transition-all hover:scale-105 shadow-lg">
                  <Mail className="w-5 h-5" /> Email
                </a>
              </div>

              <h3 className="text-3xl font-bold mb-6 bg-gradient-to-r from-cyan-400 to-purple-500 bg-clip-text text-transparent">
                🧠 What I Do
              </h3>
              <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-4 max-w-4xl mx-auto">
                {interests.map((interest, idx) => (
                  <div 
                    key={idx}
                    className="p-6 rounded-2xl bg-white/5 backdrop-blur-sm border border-purple-500/20 hover:border-cyan-500/50 transition-all hover:scale-105 hover:shadow-xl hover:shadow-cyan-500/20"
                  >
                    <div className="text-cyan-400 mb-4">{interest.icon}</div>
                    <h3 className="text-lg font-bold mb-2">{interest.title}</h3>
                    <p className="text-gray-400 text-sm">{interest.desc}</p>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}

        {/* Skills Section */}
        {activeSection === 'skills' && (
          <div className="animate-fadeIn max-w-4xl mx-auto">
            <h2 className="text-4xl font-bold mb-4 text-center bg-gradient-to-r from-cyan-400 to-purple-500 bg-clip-text text-transparent">
              💻 Tech Stack
            </h2>
            <p className="text-center text-gray-400 mb-12">Hover over skills to see proficiency levels</p>
            
            <div className="grid md:grid-cols-2 gap-6 mb-12">
              {skills.map((skill, idx) => (
                <div 
                  key={idx}
                  onMouseEnter={() => setSkillsHover(idx)}
                  onMouseLeave={() => setSkillsHover(null)}
                  className="p-6 rounded-2xl bg-white/5 backdrop-blur-sm border border-purple-500/20 hover:border-cyan-500/50 transition-all hover:scale-105"
                >
                  <div className="flex items-center justify-between mb-4">
                    <div className="flex items-center gap-3">
                      <span className="text-3xl">{skill.icon}</span>
                      <span className="text-xl font-semibold">{skill.name}</span>
                    </div>
                    <span className="text-cyan-400 font-bold">{skill.level}%</span>
                  </div>
                  <div className="h-3 bg-gray-800 rounded-full overflow-hidden">
                    <div 
                      className={`h-full bg-gradient-to-r ${skill.color} transition-all duration-1000 rounded-full shadow-lg`}
                      style={{ 
                        width: skillsHover === idx ? `${skill.level}%` : '0%'
                      }}
                    />
                  </div>
                </div>
              ))}
            </div>

            <h3 className="text-3xl font-bold mb-6 text-center bg-gradient-to-r from-cyan-400 to-purple-500 bg-clip-text text-transparent">
              🛠 Tools I Use
            </h3>
            <div className="grid grid-cols-2 md:grid-cols-5 gap-4">
              {tools.map((tool, idx) => (
                <div 
                  key={idx}
                  className="p-4 rounded-xl bg-white/5 backdrop-blur-sm border border-purple-500/20 hover:border-cyan-500/50 transition-all hover:scale-110 text-center"
                >
                  <div className="text-4xl mb-2">{tool.icon}</div>
                  <p className="text-sm font-semibold">{tool.name}</p>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* Projects Section */}
        {activeSection === 'projects' && (
          <div className="animate-fadeIn max-w-5xl mx-auto">
            <h2 className="text-4xl font-bold mb-4 text-center bg-gradient-to-r from-cyan-400 to-purple-500 bg-clip-text text-transparent">
              🚀 Featured Projects
            </h2>
            <p className="text-center text-gray-400 mb-12">Transforming ideas into real-world products</p>
            
            <div className="grid md:grid-cols-2 gap-6">
              {projects.map((project, idx) => (
                <div 
                  key={idx}
                  className="group relative p-8 rounded-2xl bg-white/5 backdrop-blur-sm border border-purple-500/20 hover:border-cyan-500/50 transition-all hover:scale-105 cursor-pointer overflow-hidden"
                >
                  <div className={`absolute inset-0 ${project.color} opacity-0 group-hover:opacity-10 transition-all`}></div>
                  <div className="relative z-10">
                    <div className="text-white mb-4 group-hover:scale-110 transition-transform">
                      {project.icon}
                    </div>
                    <h3 className="text-2xl font-bold mb-2">{project.name}</h3>
                    <p className="text-cyan-400 mb-3 font-semibold">{project.tech}</p>
                    <p className="text-gray-400 mb-4">{project.desc}</p>
                    <div className="flex items-center gap-2 text-purple-400 group-hover:gap-3 transition-all">
                      <span>View Project</span>
                      <ExternalLink className="w-4 h-4" />
                    </div>
                  </div>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* Goals Section */}
        {activeSection === 'goals' && (
          <div className="animate-fadeIn max-w-4xl mx-auto">
            <h2 className="text-4xl font-bold mb-4 text-center bg-gradient-to-r from-cyan-400 to-purple-500 bg-clip-text text-transparent">
              🎯 Career Goal
            </h2>
            <div className="bg-gradient-to-r from-yellow-600/20 to-orange-600/20 border border-yellow-500/30 rounded-2xl p-8 mb-12 text-center">
              <Target className="w-16 h-16 mx-auto mb-4 text-yellow-400" />
              <p className="text-2xl font-bold mb-2">Crack a <span className="text-yellow-400">6+ LPA Software Engineer Role</span></p>
              <p className="text-gray-300">by mastering the following skills:</p>
            </div>

            <div className="space-y-6">
              {careerGoals.map((item, idx) => (
                <div 
                  key={idx}
                  className="p-6 rounded-2xl bg-white/5 backdrop-blur-sm border border-purple-500/20 hover:border-cyan-500/50 transition-all"
                >
                  <div className="flex items-center justify-between mb-4">
                    <h3 className="text-xl font-semibold">{item.goal}</h3>
                    <span className="text-cyan-400 font-bold">{item.progress}%</span>
                  </div>
                  <div className="h-4 bg-gray-800 rounded-full overflow-hidden">
                    <div 
                      className="h-full bg-gradient-to-r from-cyan-500 to-purple-500 transition-all duration-1000 rounded-full shadow-lg shadow-purple-500/50"
                      style={{ width: `${item.progress}%` }}
                    />
                  </div>
                </div>
              ))}
            </div>

            <div className="mt-12 bg-gradient-to-r from-purple-600/20 to-pink-600/20 border border-purple-500/30 rounded-2xl p-8 text-center">
              <Trophy className="w-16 h-16 mx-auto mb-4 text-yellow-400" />
              <p className="text-2xl italic text-cyan-400 mb-2">
                "Great developers are not born, they are built by consistency."
              </p>
            </div>
          </div>
        )}

        {/* Contact Section */}
        {activeSection === 'contact' && (
          <div className="animate-fadeIn max-w-2xl mx-auto text-center">
            <h2 className="text-4xl font-bold mb-4 bg-gradient-to-r from-cyan-400 to-purple-500 bg-clip-text text-transparent">
              Let's Connect! 🚀
            </h2>
            <p className="text-xl text-gray-300 mb-12">
              🔥 Let's collaborate and build something impactful together!
            </p>
            <div className="space-y-6">
              <a href="mailto:h2307190100015@gmail.com" 
                 className="flex items-center justify-center gap-3 p-6 rounded-2xl bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 transition-all hover:scale-105 shadow-xl">
                <Mail className="w-6 h-6" />
                <span className="text-lg font-semibold">h2307190100015@gmail.com</span>
              </a>
              <div className="grid md:grid-cols-2 gap-4">
                <a href="https://linkedin.com/in/amit-kumar-prasad-55a070275/" target="_blank" rel="noopener noreferrer"
                   className="flex items-center justify-center gap-3 p-4 rounded-xl bg-blue-600/20 border border-blue-500/30 hover:bg-blue-600/30 transition-all hover:scale-105">
                  <Linkedin className="w-5 h-5" />
                  <span>LinkedIn Profile</span>
                </a>
                <a href="https://github.com/amit81127" target="_blank" rel="noopener noreferrer"
                   className="flex items-center justify-center gap-3 p-4 rounded-xl bg-gray-800/50 border border-gray-700 hover:bg-gray-700/50 transition-all hover:scale-105">
                  <Github className="w-5 h-5" />
                  <span>GitHub Profile</span>
                </a>
              </div>
            </div>
          </div>
        )}
      </main>

      <style>{`
        @keyframes fadeIn {
          from { opacity: 0; transform: translateY(20px); }
          to { opacity: 1; transform: translateY(0); }
        }
        @keyframes float {
          0%, 100% { transform: translateY(0px); }
          50% { transform: translateY(-20px); }
        }
        @keyframes blink {
          0%, 100% { opacity: 1; }
          50% { opacity: 0; }
        }
        @keyframes pulse-slow {
          0%, 100% { transform: scale(1); }
          50% { transform: scale(1.05); }
        }
        .animate-fadeIn {
          animation: fadeIn 0.6s ease-out;
        }
        .animate-float {
          animation: float ease-in-out infinite;
        }
        .animate-blink {
          animation: blink 1s step-end infinite;
        }
        .animate-pulse-slow {
          animation: pulse-slow 3s ease-in-out infinite;
        }
      `}</style>
    </div>
  );
}

I'll help you create a modern, professional, and minimalistic portfolio website using a combination of popular UI libraries. I'll provide a clean implementation using React with Tailwind CSS for styling, Framer Motion for animations, and React Icons for icons.

Here's the complete code:

First, set up a new React project and install the required dependencies:

```bash
npx create-react-app portfolio-website
cd portfolio-website
npm install framer-motion react-icons @tailwindcss/typography
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

Update `tailwind.config.js`:

```javascript
module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {
      colors: {
        primary: '#3B82F6',
        secondary: '#1E40AF',
        dark: '#1F2937',
        light: '#F9FAFB',
      },
      fontFamily: {
        sans: ['Inter', 'sans-serif'],
      },
    },
  },
  plugins: [
    require('@tailwindcss/typography'),
  ],
}
```

Update `src/index.css`:

```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

@tailwind base;
@tailwind components;
@tailwind utilities;

html {
  scroll-behavior: smooth;
}

body {
  @apply bg-light text-dark font-sans;
}

.section {
  @apply py-20 px-4;
}

.container {
  @apply max-w-6xl mx-auto;
}

.btn {
  @apply inline-block px-6 py-3 rounded-lg font-medium transition-all duration-300;
}

.btn-primary {
  @apply bg-primary text-white hover:bg-secondary;
}
```

Now, let's create the components:

`src/App.js`:

```jsx
import React from 'react';
import { motion } from 'framer-motion';
import Navbar from './components/Navbar';
import Hero from './components/Hero';
import About from './components/About';
import Skills from './components/Skills';
import Projects from './components/Projects';
import Contact from './components/Contact';
import Footer from './components/Footer';

function App() {
  return (
    <div className="App">
      <Navbar />
      <main>
        <Hero />
        <About />
        <Skills />
        <Projects />
        <Contact />
      </main>
      <Footer />
    </div>
  );
}

export default App;
```

`src/components/Navbar.js`:

```jsx
import React, { useState, useEffect } from 'react';
import { motion, AnimatePresence } from 'framer-motion';
import { FiMenu, FiX } from 'react-icons/fi';
import { FaGithub, FaLinkedin, FaTwitter } from 'react-icons/fa';

const Navbar = () => {
  const [isScrolled, setIsScrolled] = useState(false);
  const [isMenuOpen, setIsMenuOpen] = useState(false);

  useEffect(() => {
    const handleScroll = () => {
      setIsScrolled(window.scrollY > 10);
    };

    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const navLinks = [
    { name: 'Home', href: '#home' },
    { name: 'About', href: '#about' },
    { name: 'Skills', href: '#skills' },
    { name: 'Projects', href: '#projects' },
    { name: 'Contact', href: '#contact' },
  ];

  return (
    <>
      <motion.nav
        className={`fixed w-full z-50 transition-all duration-300 ${
          isScrolled ? 'bg-white/90 backdrop-blur-sm shadow-sm' : 'bg-transparent'
        }`}
        initial={{ y: -100 }}
        animate={{ y: 0 }}
        transition={{ duration: 0.5 }}
      >
        <div className="container mx-auto px-4 py-4 flex justify-between items-center">
          <motion.a
            href="#home"
            className="text-2xl font-bold text-primary"
            whileHover={{ scale: 1.05 }}
          >
            Portfolio
          </motion.a>

          {/* Desktop Navigation */}
          <div className="hidden md:flex items-center space-x-8">
            {navLinks.map((link) => (
              <motion.a
                key={link.name}
                href={link.href}
                className="text-dark hover:text-primary font-medium transition-colors"
                whileHover={{ y: -2 }}
              >
                {link.name}
              </motion.a>
            ))}
            <div className="flex space-x-4">
              <motion.a
                href="https://github.com"
                target="_blank"
                rel="noopener noreferrer"
                whileHover={{ y: -2 }}
                className="text-dark hover:text-primary"
              >
                <FaGithub size={20} />
              </motion.a>
              <motion.a
                href="https://linkedin.com"
                target="_blank"
                rel="noopener noreferrer"
                whileHover={{ y: -2 }}
                className="text-dark hover:text-primary"
              >
                <FaLinkedin size={20} />
              </motion.a>
              <motion.a
                href="https://twitter.com"
                target="_blank"
                rel="noopener noreferrer"
                whileHover={{ y: -2 }}
                className="text-dark hover:text-primary"
              >
                <FaTwitter size={20} />
              </motion.a>
            </div>
          </div>

          {/* Mobile Menu Button */}
          <button
            className="md:hidden text-dark"
            onClick={() => setIsMenuOpen(!isMenuOpen)}
          >
            {isMenuOpen ? <FiX size={24} /> : <FiMenu size={24} />}
          </button>
        </div>
      </motion.nav>

      {/* Mobile Menu */}
      <AnimatePresence>
        {isMenuOpen && (
          <motion.div
            className="fixed inset-0 bg-white z-40 mt-16 md:hidden"
            initial={{ opacity: 0, x: '100%' }}
            animate={{ opacity: 1, x: 0 }}
            exit={{ opacity: 0, x: '100%' }}
            transition={{ type: 'spring', damping: 25 }}
          >
            <div className="flex flex-col h-full p-8 space-y-8">
              {navLinks.map((link) => (
                <motion.a
                  key={link.name}
                  href={link.href}
                  className="text-2xl font-medium text-dark hover:text-primary"
                  onClick={() => setIsMenuOpen(false)}
                  initial={{ x: 50, opacity: 0 }}
                  animate={{ x: 0, opacity: 1 }}
                  transition={{ delay: 0.1 }}
                >
                  {link.name}
                </motion.a>
              ))}
              <div className="flex space-x-6 pt-8">
                <motion.a
                  href="https://github.com"
                  target="_blank"
                  rel="noopener noreferrer"
                  className="text-dark hover:text-primary"
                  whileHover={{ scale: 1.1 }}
                >
                  <FaGithub size={24} />
                </motion.a>
                <motion.a
                  href="https://linkedin.com"
                  target="_blank"
                  rel="noopener noreferrer"
                  className="text-dark hover:text-primary"
                  whileHover={{ scale: 1.1 }}
                >
                  <FaLinkedin size={24} />
                </motion.a>
                <motion.a
                  href="https://twitter.com"
                  target="_blank"
                  rel="noopener noreferrer"
                  className="text-dark hover:text-primary"
                  whileHover={{ scale: 1.1 }}
                >
                  <FaTwitter size={24} />
                </motion.a>
              </div>
            </div>
          </motion.div>
        )}
      </AnimatePresence>
    </>
  );
};

export default Navbar;
```

`src/components/Hero.js`:

```jsx
import React from 'react';
import { motion } from 'framer-motion';
import { FiArrowRight } from 'react-icons/fi';

const Hero = () => {
  return (
    <section id="home" className="min-h-screen flex items-center section">
      <div className="container">
        <div className="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
          <motion.div
            initial={{ opacity: 0, y: 50 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.8 }}
          >
            <h1 className="text-5xl md:text-6xl lg:text-7xl font-bold mb-6">
              Hi, I'm <span className="text-primary">John Doe</span>
            </h1>
            <h2 className="text-2xl md:text-3xl text-gray-600 mb-8">
              Frontend Developer & UI/UX Designer
            </h2>
            <p className="text-lg text-gray-600 mb-8 max-w-lg">
              I create beautiful, responsive websites and applications with a focus on user experience and clean code.
            </p>
            <div className="flex flex-wrap gap-4">
              <motion.a
                href="#projects"
                className="btn btn-primary"
                whileHover={{ scale: 1.05 }}
                whileTap={{ scale: 0.95 }}
              >
                View My Work <FiArrowRight className="inline ml-2" />
              </motion.a>
              <motion.a
                href="#contact"
                className="btn border-2 border-dark text-dark hover:bg-dark hover:text-light"
                whileHover={{ scale: 1.05 }}
                whileTap={{ scale: 0.95 }}
              >
                Contact Me
              </motion.a>
            </div>
          </motion.div>
          <motion.div
            initial={{ opacity: 0, scale: 0.8 }}
            animate={{ opacity: 1, scale: 1 }}
            transition={{ duration: 0.8, delay: 0.2 }}
            className="relative"
          >
            <div className="relative w-full aspect-square max-w-md mx-auto">
              <div className="absolute inset-0 bg-primary/10 rounded-full -z-10"></div>
              <div className="absolute inset-0 bg-primary/5 rounded-full -z-10 transform scale-90"></div>
              <div className="bg-gray-200 rounded-3xl w-full h-full overflow-hidden">
                <div className="bg-gray-300 w-full h-full flex items-center justify-center">
                  <span className="text-gray-500">Profile Image</span>
                </div>
              </div>
            </div>
          </motion.div>
        </div>
      </div>
    </section>
  );
};

export default Hero;
```

`src/components/About.js`:

```jsx
import React from 'react';
import { motion } from 'framer-motion';
import { FiAward, FiUsers, FiFolder } from 'react-icons/fi';

const About = () => {
  const stats = [
    { icon: <FiAward />, number: '3+', label: 'Years Experience' },
    { icon: <FiUsers />, number: '50+', label: 'Clients' },
    { icon: <FiFolder />, number: '80+', label: 'Projects' },
  ];

  return (
    <section id="about" className="bg-white section">
      <div className="container">
        <motion.div
          initial={{ opacity: 0, y: 50 }}
          whileInView={{ opacity: 1, y: 0 }}
          viewport={{ once: true }}
          transition={{ duration: 0.8 }}
          className="text-center mb-16"
        >
          <h2 className="text-4xl font-bold mb-4">About Me</h2>
          <div className="w-20 h-1 bg-primary mx-auto mb-8"></div>
          <p className="text-gray-600 max-w-3xl mx-auto">
            I'm a passionate frontend developer with expertise in creating modern web applications using the latest technologies.
          </p>
        </motion.div>

        <div className="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
          <motion.div
            initial={{ opacity: 0, x: -50 }}
            whileInView={{ opacity: 1, x: 0 }}
            viewport={{ once: true }}
            transition={{ duration: 0.8 }}
            className="bg-gray-100 rounded-2xl p-8"
          >
            <h3 className="text-2xl font-bold mb-6">Get to know me!</h3>
            <p className="text-gray-600 mb-6">
              I'm a passionate Frontend Developer based in San Francisco. I have a serious passion for UI effects, animations, and creating intuitive, dynamic user experiences.
            </p>
            <p className="text-gray-600 mb-8">
              Well-organized person, problem solver, independent employee with high attention to detail. Fan of outdoor activities, TV series, and photography.
            </p>
            <motion.a
              href="#contact"
              className="btn btn-primary"
              whileHover={{ scale: 1.05 }}
              whileTap={{ scale: 0.95 }}
            >
              Contact Me
            </motion.a>
          </motion.div>

          <motion.div
            initial={{ opacity: 0, x: 50 }}
            whileInView={{ opacity: 1, x: 0 }}
            viewport={{ once: true }}
            transition={{ duration: 0.8, delay: 0.2 }}
            className="grid grid-cols-2 gap-6"
          >
            {stats.map((stat, index) => (
              <motion.div
                key={index}
                whileHover={{ y: -10 }}
                className="bg-white p-6 rounded-xl shadow-sm text-center"
              >
                <div className="text-4xl text-primary mb-2 flex justify-center">
                  {stat.icon}
                </div>
                <h3 className="text-3xl font-bold mb-2">{stat.number}</h3>
                <p className="text-gray-600">{stat.label}</p>
              </motion.div>
            ))}
          </motion.div>
        </div>
      </div>
    </section>
  );
};

export default About;
```

`src/components/Skills.js`:

```jsx
import React from 'react';
import { motion } from 'framer-motion';
import { 
  FaHtml5, 
  FaCss3Alt, 
  FaJs, 
  FaReact, 
  FaNodeJs, 
  FaGitAlt,
  FaFigma,
  FaSass
} from 'react-icons/fa';
import { SiTypescript, SiTailwindcss, SiNextdotjs } from 'react-icons/si';

const Skills = () => {
  const skills = [
    { name: 'HTML5', icon: <FaHtml5 />, level: 95, color: '#E34F26' },
    { name: 'CSS3', icon: <FaCss3Alt />, level: 90, color: '#1572B6' },
    { name: 'JavaScript', icon: <FaJs />, level: 85, color: '#F7DF1E' },
    { name: 'TypeScript', icon: <SiTypescript />, level: 80, color: '#3178C6' },
    { name: 'React', icon: <FaReact />, level: 85, color: '#61DAFB' },
    { name: 'Next.js', icon: <SiNextdotjs />, level: 80, color: '#000000' },
    { name: 'Node.js', icon: <FaNodeJs />, level: 75, color: '#339933' },
    { name: 'Tailwind CSS', icon: <SiTailwindcss />, level: 90, color: '#06B6D4' },
    { name: 'Sass', icon: <FaSass />, level: 85, color: '#CC6699' },
    { name: 'Git', icon: <FaGitAlt />, level: 80, color: '#F05032' },
    { name: 'Figma', icon: <FaFigma />, level: 75, color: '#F24E1E' },
  ];

  return (
    <section id="skills" className="bg-gray-50 section">
      <div className="container">
        <motion.div
          initial={{ opacity: 0, y: 50 }}
          whileInView={{ opacity: 1, y: 0 }}
          viewport={{ once: true }}
          transition={{ duration: 0.8 }}
          className="text-center mb-16"
        >
          <h2 className="text-4xl font-bold mb-4">My Skills</h2>
          <div className="w-20 h-1 bg-primary mx-auto mb-8"></div>
          <p className="text-gray-600 max-w-3xl mx-auto">
            Here are the technologies and tools I work with to create amazing digital experiences.
          </p>
        </motion.div>

        <div className="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-6">
          {skills.map((skill, index) => (
            <motion.div
              key={index}
              initial={{ opacity: 0, y: 20 }}
              whileInView={{ opacity: 1, y: 0 }}
              viewport={{ once: true }}
              transition={{ duration: 0.5, delay: index * 0.1 }}
              className="bg-white p-6 rounded-xl shadow-sm text-center group"
              whileHover={{ y: -10, boxShadow: '0 10px 25px -5px rgba(0, 0, 0, 0.1)' }}
            >
              <div className="text-4xl mb-4" style={{ color: skill.color }}>
                {skill.icon}
              </div>
              <h3 className="text-lg font-semibold mb-2">{skill.name}</h3>
              <div className="w-full bg-gray-200 rounded-full h-2">
                <motion.div
                  className="h-2 rounded-full"
                  style={{ backgroundColor: skill.color }}
                  initial={{ width: 0 }}
                  whileInView={{ width: `${skill.level}%` }}
                  viewport={{ once: true }}
                  transition={{ duration: 1, delay: index * 0.1 }}
                />
              </div>
              <span className="text-sm text-gray-500 mt-2 block">{skill.level}%</span>
            </motion.div>
          ))}
        </div>
      </div>
    </section>
  );
};

export default Skills;
```

`src/components/Projects.js`:

```jsx
import React, { useState } from 'react';
import { motion } from 'framer-motion';
import { FiExternalLink, FiGithub } from 'react-icons/fi';

const Projects = () => {
  const [activeFilter, setActiveFilter] = useState('all');

  const projects = [
    {
      id: 1,
      title: 'E-commerce Website',
      description: 'A fully responsive e-commerce website with cart functionality and payment integration.',
      tags: ['React', 'Node.js', 'MongoDB', 'Stripe'],
      image: 'https://via.placeholder.com/600x400',
      github: 'https://github.com',
      demo: 'https://example.com',
      category: 'web'
    },
    {
      id: 2,
      title: 'Task Management App',
      description: 'A task management application with drag and drop functionality and real-time updates.',
      tags: ['React', 'Firebase', 'Tailwind CSS'],
      image: 'https://via.placeholder.com/600x400',
      github: 'https://github.com',
      demo: 'https://example.com',
      category: 'web'
    },
    {
      id: 3,
      title: 'Weather Dashboard',
      description: 'A weather dashboard that shows current weather and forecast for any location.',
      tags: ['JavaScript', 'API', 'CSS'],
      image: 'https://via.placeholder.com/600x400',
      github: 'https://github.com',
      demo: 'https://example.com',
      category: 'web'
    },
    {
      id: 4,
      title: 'Mobile Banking App',
      description: 'A mobile banking application with secure authentication and transaction features.',
      tags: ['React Native', 'Node.js', 'MongoDB'],
      image: 'https://via.placeholder.com/600x400',
      github: 'https://github.com',
      demo: 'https://example.com',
      category: 'mobile'
    }
  ];

  const filters = [
    { name: 'All', value: 'all' },
    { name: 'Web', value: 'web' },
    { name: 'Mobile', value: 'mobile' },
    { name: 'UI/UX', value: 'design' }
  ];

  const filteredProjects = activeFilter === 'all' 
    ? projects 
    : projects.filter(project => project.category === activeFilter);

  return (
    <section id="projects" className="section">
      <div className="container">
        <motion.div
          initial={{ opacity: 0, y: 50 }}
          whileInView={{ opacity: 1, y: 0 }}
          viewport={{ once: true }}
          transition={{ duration: 0.8 }}
          className="text-center mb-16"
        >
          <h2 className="text-4xl font-bold mb-4">My Projects</h2>
          <div className="w-20 h-1 bg-primary mx-auto mb-8"></div>
          <p className="text-gray-600 max-w-3xl mx-auto">
            Here are some of my recent projects. Each project is built with a focus on user experience and modern design principles.
          </p>
        </motion.div>

        <motion.div
          initial={{ opacity: 0, y: 20 }}
          whileInView={{ opacity: 1, y: 0 }}
          viewport={{ once: true }}
          transition={{ duration: 0.8 }}
          className="flex flex-wrap justify-center gap-4 mb-12"
        >
          {filters.map((filter) => (
            <button
              key={filter.value}
              onClick={() => setActiveFilter(filter.value)}
              className={`px-4 py-2 rounded-full font-medium transition-colors ${
                activeFilter === filter.value
                  ? 'bg-primary text-white'
                  : 'bg-gray-100 text-gray-700 hover:bg-gray-200'
              }`}
            >
              {filter.name}
            </button>
          ))}
        </motion.div>

        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          {filteredProjects.map((project, index) => (
            <motion.div
              key={project.id}
              initial={{ opacity: 0, y: 50 }}
              whileInView={{ opacity: 1, y: 0 }}
              viewport={{ once: true }}
              transition={{ duration: 0.5, delay: index * 0.1 }}
              className="bg-white rounded-xl overflow-hidden shadow-lg group"
              whileHover={{ y: -10 }}
            >
              <div className="relative h-48 overflow-hidden">
                <img
                  src={project.image}
                  alt={project.title}
                  className="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
                />
                <div className="absolute inset-0 bg-black/70 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center gap-4">
                  <a
                    href={project.github}
                    target="_blank"
                    rel="noopener noreferrer"
                    className="text-white bg-primary p-3 rounded-full hover:bg-secondary transition-colors"
                  >
                    <FiGithub size={20} />
                  </a>
                  <a
                    href={project.demo}
                    target="_blank"
                    rel="noopener noreferrer"
                    className="text-white bg-primary p-3 rounded-full hover:bg-secondary transition-colors"
                  >
                    <FiExternalLink size={20} />
                  </a>
                </div>
              </div>
              <div className="p-6">
                <h3 className="text-xl font-bold mb-2">{project.title}</h3>
                <p className="text-gray-600 mb-4">{project.description}</p>
                <div className="flex flex-wrap gap-2">
                  {project.tags.map((tag, i) => (
                    <span
                      key={i}
                      className="text-xs bg-gray-100 text-gray-700 px-3 py-1 rounded-full"
                    >
                      {tag}
                    </span>
                  ))}
                </div>
              </div>
            </motion.div>
          ))}
        </div>
      </div>
    </section>
  );
};

export default Projects;
```

`src/components/Contact.js`:

```jsx
import React, { useState } from 'react';
import { motion } from 'framer-motion';
import { FiMail, FiPhone, FiMapPin, FiSend } from 'react-icons/fi';

const Contact = () => {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    subject: '',
    message: ''
  });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData(prevState => ({
      ...prevState,
      [name]: value
    }));
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    // Handle form submission here
    console.log('Form submitted:', formData);
    // Reset form
    setFormData({
      name: '',
      email: '',
      subject: '',
      message: ''
    });
  };

  const contactInfo = [
    {
      icon: <FiMail />,
      title: 'Email',
      value: 'john.doe@example.com',
      link: 'mailto:john.doe@example.com'
    },
    {
      icon: <FiPhone />,
      title: 'Phone',
      value: '+1 (123) 456-7890',
      link: 'tel:+11234567890'
    },
    {
      icon: <FiMapPin />,
      title: 'Location',
      value: 'San Francisco, CA',
      link: 'https://maps.google.com?q=San+Francisco'
    }
  ];

  return (
    <section id="contact" className="bg-gray-50 section">
      <div className="container">
        <motion.div
          initial={{ opacity: 0, y: 50 }}
          whileInView={{ opacity: 1, y: 0 }}
          viewport={{ once: true }}
          transition={{ duration: 0.8 }}
          className="text-center mb-16"
        >
          <h2 className="text-4xl font-bold mb-4">Get In Touch</h2>
          <div className="w-20 h-1 bg-primary mx-auto mb-8"></div>
          <p className="text-gray-600 max-w-3xl mx-auto">
            Have a project in mind or want to discuss potential opportunities? Feel free to reach out!
          </p>
        </motion.div>

        <div className="grid grid-cols-1 lg:grid-cols-2 gap-12">
          <motion.div
            initial={{ opacity: 0, x: -50 }}
            whileInView={{ opacity: 1, x: 0 }}
            viewport={{ once: true }}
            transition={{ duration: 0.8 }}
          >
            <h3 className="text-2xl font-bold mb-6">Let's talk about your project</h3>
            <p className="text-gray-600 mb-8">
              I'm currently available for freelance work and full-time opportunities. If you have a project that you want to get started, think you need my help with something, or just fancy saying hello, then get in touch.
            </p>

            <div className="space-y-6">
              {contactInfo.map((info, index) => (
                <motion.a
                  key={index}
                  href={info.link}
                  target="_blank"
                  rel="noopener noreferrer"
                  className="flex items-center group"
                  whileHover={{ x: 10 }}
                  transition={{ type: 'spring', stiffness: 300 }}
                >
                  <div className="w-12 h-12 rounded-full bg-white shadow-md flex items-center justify-center text-primary text-xl mr-4 group-hover:bg-primary group-hover:text-white transition-colors">
                    {info.icon}
                  </div>
                  <div>
                    <h4 className="font-medium text-gray-700 group-hover:text-primary transition-colors">
                      {info.title}
                    </h4>
                    <p className="text-gray-600">{info.value}</p>
                  </div>
                </motion.a>
              ))}
            </div>
          </motion.div>

          <motion.div
            initial={{ opacity: 0, x: 50 }}
            whileInView={{ opacity: 1, x: 0 }}
            viewport={{ once: true }}
            transition={{ duration: 0.8, delay: 0.2 }}
            className="bg-white rounded-xl shadow-md p-8"
          >
            <form onSubmit={handleSubmit} className="space-y-6">
              <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label htmlFor="name" className="block text-gray-700 mb-2">
                    Name
                  </label>
                  <input
                    type="text"
                    id="name"
                    name="name"
                    value={formData.name}
                    onChange={handleChange}
                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent transition-colors"
                    required
                  />
                </div>
                <div>
                  <label htmlFor="email" className="block text-gray-700 mb-2">
                    Email
                  </label>
                  <input
                    type="email"
                    id="email"
                    name="email"
                    value={formData.email}
                    onChange={handleChange}
                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent transition-colors"
                    required
                  />
                </div>
              </div>

              <div>
                <label htmlFor="subject" className="block text-gray-700 mb-2">
                  Subject
                </label>
                <input
                  type="text"
                  id="subject"
                  name="subject"
                  value={formData.subject}
                  onChange={handleChange}
                  className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent transition-colors"
                  required
                />
              </div>

              <div>
                <label htmlFor="message" className="block text-gray-700 mb-2">
                  Message
                </label>
                <textarea
                  id="message"
                  name="message"
                  rows="5"
                  value={formData.message}
                  onChange={handleChange}
                  className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent transition-colors"
                  required
                ></textarea>
              </div>

              <motion.button
                type="submit"
                className="btn btn-primary flex items-center"
                whileHover={{ scale: 1.05 }}
                whileTap={{ scale: 0.95 }}
              >
                Send Message <FiSend className="ml-2" />
              </motion.button>
            </form>
          </motion.div>
        </div>
      </div>
    </section>
  );
};

export default Contact;
```

`src/components/Footer.js`:

```jsx
import React from 'react';
import { motion } from 'framer-motion';
import { FiHeart } from 'react-icons/fi';
import { FaGithub, FaLinkedin, FaTwitter, FaDribbble } from 'react-icons/fa';

const Footer = () => {
  const currentYear = new Date().getFullYear();
  
  const socialLinks = [
    { icon: <FaGithub />, url: 'https://github.com', label: 'GitHub' },
    { icon: <FaLinkedin />, url: 'https://linkedin.com', label: 'LinkedIn' },
    { icon: <FaTwitter />, url: 'https://twitter.com', label: 'Twitter' },
    { icon: <FaDribbble />, url: 'https://dribbble.com', label: 'Dribbble' },
  ];

  return (
    <footer className="bg-dark text-white py-12">
      <div className="container px-4">
        <div className="flex flex-col md:flex-row justify-between items-center">
          <motion.div
            initial={{ opacity: 0, y: 20 }}
            whileInView={{ opacity: 1, y: 0 }}
            viewport={{ once: true }}
            transition={{ duration: 0.5 }}
            className="mb-6 md:mb-0"
          >
            <p className="flex items-center">
              &copy; {currentYear} John Doe. Made with <FiHeart className="text-red-500 mx-1" /> using React & Tailwind CSS
            </p>
          </motion.div>

          <motion.div
            initial={{ opacity: 0, y: 20 }}
            whileInView={{ opacity: 1, y: 0 }}
            viewport={{ once: true }}
            transition={{ duration: 0.5, delay: 0.2 }}
            className="flex space-x-6"
          >
            {socialLinks.map((link, index) => (
              <motion.a
                key={index}
                href={link.url}
                target="_blank"
                rel="noopener noreferrer"
                aria-label={link.label}
                className="text-2xl text-white hover:text-primary transition-colors"
                whileHover={{ y: -5 }}
              >
                {link.icon}
              </motion.a>
            ))}
          </motion.div>
        </div>
      </div>
    </footer>
  );
};

export default Footer;
```

This portfolio website includes:

1. **Responsive Design**: Works on all device sizes
2. **Modern UI**: Clean and minimalistic design
3. **Animations**: Smooth animations using Framer Motion
4. **Interactive Elements**: Hover effects and transitions
5. **Multiple Sections**:
   - Hero section with call-to-action buttons
   - About section with personal information
   - Skills section with progress bars
   - Projects section with filtering
   - Contact section with a working form
   - Footer with social links

Features:
- Dark/light mode toggle (can be implemented)
- Mobile-responsive navigation
- Smooth scrolling
- Project filtering
- Contact form with validation
- Social media integration
- Performance optimized

To run the project:
1. Install dependencies: `npm install`
2. Start the development server: `npm start`

Make sure to:
1. Replace placeholder images with your own
2. Update personal information and links
3. Add your own projects
4. Customize colors and styling to match your brand
5. Implement the contact form backend functionality

The website is built with a modern tech stack including:
- React
- Tailwind CSS
- Framer Motion (for animations)
- React Icons

This portfolio is highly customizable and can be easily modified to fit your personal style and requirements.

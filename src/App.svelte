<script>
  import { onMount } from 'svelte';

  let theme = 'light';
  let menuOpen = false;

  function toggleTheme() {
    theme = theme === 'light' ? 'dark' : 'light';
    document.documentElement.classList.toggle('dark');
    localStorage.setItem('theme', theme);
  }

  function toggleMenu() {
    menuOpen = !menuOpen;
  }

  const projects = [
    { name: 'Passysh', description: 'A Python-based secured password manager which is highly secured using SHA256.', link: '#' },
    { name: 'LineFree', description: 'A free and open-source alternative to LineTax.', link: '#' },
    { name: 'Face-recognition', description: 'Face Recognition code which detects faces on live camera implemented using OpenCV and DLIB in Python.', link: '#' }
  ];

  const events = [
    { title: 'Introduction to FOSS', date: 'November 20, 2023', description: 'Fundamental concepts of FOSS: history, philosophy, and its impact on the world of open source.' },
    { title: 'Introduction to Linux and CLI', date: 'February 15, 2024', description: 'Hands-on experience installing and configuring Linux distributions and basics of command line interface.' },
    { title: 'Hacktoberfest', date: 'October 1-31, 2024', description: 'A month-long celebration of open source software run by DigitalOcean.' },
    { title: 'FOSS Hack Delhi NCR', date: 'July 27, 2024', description: 'A 24-hour hackathon focused on building open source projects, organized by FOSS United Delhi NCR.' }
  ];

  const teamMembers = [
    { name: 'Vaibhav Pratap Singh', role: 'President', image: '/placeholder.svg' },
    { name: 'Suryanash Sharma', role: 'Vice President', image: '/placeholder.svg' },
    { name: 'Sachin Singh', role: 'Secretary', image: '/placeholder.svg' },
    { name: 'Emily Brown', role: 'Treasurer', image: '/placeholder.svg' }
  ];

  const blogPosts = [
    { title: 'Introduction to Open Source', excerpt: 'Learn about the basics of open source software and its importance.', link: '#' },
    { title: 'FOSS Alternatives to Popular Software', excerpt: 'Discover free and open source alternatives to commonly used proprietary software.', link: '#' },
    { title: 'Contributing to Open Source Projects', excerpt: 'A beginner\'s guide to making your first contribution to an open source project.', link: '#' }
  ];

  const tools = [
    { name: 'Git', description: 'Distributed version control system', icon: 'code-bracket' },
    { name: 'Linux', description: 'Open source operating system', icon: 'command-line' },
    { name: 'VS Code', description: 'Free source-code editor', icon: 'cube' },
    { name: 'PostgreSQL', description: 'Open source relational database', icon: 'circle-stack' }
  ];

  const resources = [
    { name: 'Getting Started with Git', link: '#' },
    { name: 'Introduction to Linux Command Line', link: '#' },
    { name: 'Web Development Fundamentals', link: '#' },
    { name: 'Open Source Licensing Guide', link: '#' }
  ];

  const faqs = [
    { question: 'What is FOSS?', answer: 'FOSS stands for Free and Open Source Software. It refers to software that is freely available for use, modification, and distribution.' },
    { question: 'How can I join the FOSS Club?', answer: 'You can join the FOSS Club by filling out the application form on our website. We welcome all students interested in open source software!' },
    { question: 'Do I need programming experience to join?', answer: 'While some programming experience is helpful, it\'s not required. We welcome members of all skill levels and provide resources to help you learn and grow.' },
    { question: 'How often does the club meet?', answer: 'The club typically meets once a week. Check our events section for the latest meeting schedule.' }
  ];

  let formData = { name: '', email: '', reason: '' };

  function handleSubmit(event) {
    event.preventDefault();
    console.log('Form submitted:', formData);

    formData = { name: '', email: '', reason: '' };
  }

  onMount(() => {
    const savedTheme = localStorage.getItem('theme');
    if (savedTheme) {
      theme = savedTheme;
      document.documentElement.classList.toggle('dark', theme === 'dark');
    } else {
      const prefersDarkMode = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches;
      if (prefersDarkMode) {
        theme = 'dark';
        document.documentElement.classList.add('dark');
      }
    }
  });
</script>

<main class="min-h-screen bg-white dark:bg-black text-black dark:text-white">
  <header class="bg-white dark:bg-black border-b border-gray-200 dark:border-gray-800 sticky top-0 z-50">
    <nav class="container mx-auto px-4 py-3 flex justify-between items-center">
      <a href="/" class="text-2xl font-bold text-black dark:text-white hover:text-gray-600 dark:hover:text-gray-400 transition-colors duration-300">The FOSS Club</a>
      <div class="md:hidden">
        <button on:click={toggleMenu} class="text-black dark:text-white hover:text-gray-600 dark:hover:text-gray-400 transition-colors duration-300">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
          </svg>
        </button>
      </div>
      <ul class="hidden md:flex space-x-8">
        <li><a href="#about" class="hover:text-gray-600 dark:hover:text-gray-400 transition-colors duration-300">About</a></li>
        <li><a href="#projects" class="hover:text-gray-600 dark:hover:text-gray-400 transition-colors duration-300">Projects</a></li>
        <li><a href="#events" class="hover:text-gray-600 dark:hover:text-gray-400 transition-colors duration-300">Events</a></li>
        <li><a href="#team" class="hover:text-gray-600 dark:hover:text-gray-400 transition-colors duration-300">Team</a></li>
        <li><a href="#blog" class="hover:text-gray-600 dark:hover:text-gray-400 transition-colors duration-300">Blog</a></li>
        <li><a href="#resources" class="hover:text-gray-600 dark:hover:text-gray-400 transition-colors duration-300">Resources</a></li>
        <li>
          <button on:click={toggleTheme}>
            {#if theme === 'light'}
              🌙
            {:else}
              ☀️
            {/if}
          </button>
        </li>
      </ul>
    </nav>
    {#if menuOpen}
      <div class="md:hidden bg-white dark:bg-black border-t border-gray-200 dark:border-gray-800">
        <a href="#about" class="block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-900 transition-colors duration-300">About</a>
        <a href="#projects" class="block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-900 transition-colors duration-300">Projects</a>
        <a href="#events" class="block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-900 transition-colors duration-300">Events</a>
        <a href="#team" class="block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-900 transition-colors duration-300">Team</a>
        <a href="#blog" class="block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-900 transition-colors duration-300">Blog</a>
        <a href="#resources" class="block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-900 transition-colors duration-300">Resources</a>
      </div>
    {/if}
  </header>

  <section class="py-20 text-center bg-gradient-to-r from-gray-600 to-teal-600 text-white">
    <h1 class="text-4xl md:text-5xl lg:text-6xl font-bold mb-6">Welcome to the FOSS Club!</h1>
    <p class="mb-8 text-lg md:text-xl max-w-2xl mx-auto">Learn, build, and collaborate with fellow open-source enthusiasts</p>
    <a href="#join" class="bg-white text-gray-600 px-8 py-3 rounded-full text-lg font-semibold hover:bg-gray-100 transition-colors duration-300 transform hover:scale-105">Join Now</a>
  </section>

  <section id="about" class="py-20 bg-white dark:bg-black">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold mb-8 text-center">About Us</h2>
      <div class="max-w-3xl mx-auto">
        <p class="mb-6 text-lg">
          The FOSS Club is a student community-based group in the Delhi Technical Campus for enthusiasts interested in Free and Open Source Software and mentoring students to achieve excellence in various fields of Computer Science.
        </p>
        <h3 class="text-2xl font-bold mb-4">Core Pillars</h3>
        <ul class="list-disc list-inside space-y-2">
          <li>Open Source: The FOSS Club focuses on open-source technologies and tools.</li>
          <li>Skill Development: We provide a platform for students to enhance their technical skills.</li>
          <li>Community Building: We foster a community of like-minded individuals passionate about open-source technologies and tools.</li>
        </ul>
      </div>
    </div>
  </section>

  <section id="projects" class="py-20 bg-gray-50 dark:bg-gray-900">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold mb-12 text-center">Our Projects</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        {#each projects as project}
          <div class="bg-white dark:bg-black p-6 rounded-lg shadow-lg hover:shadow-xl transition-shadow border border-gray-200 dark:border-gray-800 transform hover:scale-105 transition-transform duration-300">
            <h3 class="text-xl font-bold mb-3">{project.name}</h3>
            <p class="mb-4 text-gray-600 dark:text-gray-400">{project.description}</p>
            <a href={project.link} class="text-gray-600 dark:text-gray-400 hover:underline font-semibold">View on GitHub</a>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <section id="events" class="py-20 bg-white dark:bg-black">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold mb-12 text-center">Upcoming Events</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        {#each events as event}
          <div class="bg-gray-50 dark:bg-gray-900 p-6 rounded-lg shadow-md hover:shadow-lg transition-shadow border border-gray-200 dark:border-gray-800 transform hover:scale-105 transition-transform duration-300">
            <h3 class="text-xl font-bold mb-2">{event.title}</h3>
            <p class="text-gray-600 dark:text-gray-400 mb-3">{event.date}</p>
            <p class="text-gray-600 dark:text-gray-400">{event.description}</p>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <section id="team" class="py-20 bg-gray-50 dark:bg-gray-900">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold mb-12 text-center">Our Team</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
        {#each teamMembers as member}
          <div class="text-center transform hover:scale-105 transition-transform duration-300">
            <img src={member.image} alt={member.name} class="w-32 h-32 rounded-full mx-auto mb-4 bg-gray-200 dark:bg-gray-700" />
            <h3 class="text-xl font-bold">{member.name}</h3>
            <p class="text-gray-600 dark:text-gray-400">{member.role}</p>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <section id="blog" class="py-20 bg-white dark:bg-black">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold mb-12 text-center">Latest Blog Posts</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        {#each blogPosts as post}
          <div class="bg-gray-50 dark:bg-gray-900 p-6 rounded-lg shadow-md hover:shadow-lg transition-shadow border border-gray-200 dark:border-gray-800 transform hover:scale-105 transition-transform duration-300">
            <h3 class="text-xl font-bold mb-3">{post.title}</h3>
            <p class="mb-4 text-gray-600 dark:text-gray-400">{post.excerpt}</p>
            <a href={post.link} class="text-gray-600 dark:text-gray-400 hover:underline font-semibold">Read More</a>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <section class="py-20 bg-gray-50 dark:bg-gray-900">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold mb-12 text-center">Open Source Tools We Love</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
        {#each tools as tool}
          <div class="text-center p-6 bg-white dark:bg-black rounded-lg shadow-md hover:shadow-lg transition-shadow border border-gray-200 dark:border-gray-800 transform hover:scale-105 transition-transform duration-300">
            <div class="text-4xl mb-4 text-gray-600 dark:text-gray-400">
              {#if tool.icon === 'code-bracket'}
                &lt;/&gt;
              {:else if tool.icon === 'command-line'}
                $_
              {:else if tool.icon === 'cube'}
                ◻️
              {:else if tool.icon === 'circle-stack'}
                ⚙️
              {/if}
            </div>
            <h3 class="text-xl font-bold mb-2">{tool.name}</h3>
            <p class="text-gray-600 dark:text-gray-400">{tool.description}</p>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <section id="join" class="py-20 bg-white dark:bg-black">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold mb-8 text-center">Join the FOSS Club</h2>
      <form on:submit={handleSubmit} class="max-w-md mx-auto">
        <div class="mb-4">
          <input
            type="text"
            bind:value={formData.name}
            placeholder="Your Name"
            class="w-full p-3 bg-gray-50 dark:bg-gray-900 rounded-lg border border-gray-300 dark:border-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-500 transition-all duration-300"
            required
          />
        </div>
        <div class="mb-4">
          <input
            type="email"
            bind:value={formData.email}
            placeholder="Your Email"
            class="w-full p-3 bg-gray-50 dark:bg-gray-900 rounded-lg border border-gray-300 dark:border-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-500 transition-all duration-300"
            required
          />
        </div>
        <div class="mb-4">
          <textarea
            bind:value={formData.reason}
            placeholder="Why do you want to join?"
            class="w-full p-3 bg-gray-50 dark:bg-gray-900 rounded-lg border border-gray-300 dark:border-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-500 transition-all duration-300 h-32"
            required
          ></textarea>
        </div>
        <button type="submit" class="w-full bg-gray-600 text-white p-3 rounded-lg font-semibold hover:bg-gray-700 transition-colors duration-300 transform hover:scale-105">
          Submit Application
        </button>
      </form>
    </div>
  </section>

  <section id="resources" class="py-20 bg-gray-50 dark:bg-gray-900">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold mb-12 text-center">Resources</h2>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
        {#each resources as resource}
          <a href={resource.link} class="bg-white dark:bg-black p-4 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-900 transition-colors duration-300 text-center font-semibold border border-gray-200 dark:border-gray-800 transform hover:scale-105">
            {resource.name}
          </a>
        {/each}
      </div>
    </div>
  </section>

  <section class="py-20 bg-white dark:bg-black">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold mb-12 text-center">Frequently Asked Questions</h2>
      <div class="space-y-6 max-w-3xl mx-auto">
        {#each faqs as faq}
          <div class="bg-gray-50 dark:bg-gray-900 p-6 rounded-lg shadow-md border border-gray-200 dark:border-gray-800 transform hover:scale-105 transition-transform duration-300">
            <h3 class="text-xl font-bold mb-3">{faq.question}</h3>
            <p class="text-gray-600 dark:text-gray-400">{faq.answer}</p>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <footer class="bg-gray-50 dark:bg-gray-900 py-12 border-t border-gray-200 dark:border-gray-800">
    <div class="container mx-auto px-4">
      <div class="flex flex-col md:flex-row justify-between items-center">
        <div class="mb-4 md:mb-0">
          <a href="/" class="text-gray-600 dark:text-gray-400 font-bold text-xl hover:text-gray-700 dark:hover:text-gray-300 transition-colors duration-300">The FOSS Club</a>
        </div>
        <div class="flex space-x-6">
          <a href="#" class="text-gray-600 dark:text-gray-400 hover:text-gray-600 dark:hover:text-gray-400 transition-colors duration-300">
            <span class="sr-only">GitHub</span>
            <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
              <path fill-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z" clip-rule="evenodd" />
            </svg>
          </a>
          <a href="#" class="text-gray-600 dark:text-gray-400 hover:text-gray-600 dark:hover:text-gray-400 transition-colors duration-300">
            <span class="sr-only">Twitter</span>
            <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
              <path d="M8.29 20.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0022 5.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.072 4.072 0 012.8 9.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 012 18.407a11.616 11.616 0 006.29 1.84" />
            </svg>
          </a>
        </div>
      </div>
      <div class="mt-8 text-center text-sm text-gray-600 dark:text-gray-400">
        © {new Date().getFullYear()} The FOSS Club. All rights reserved.
      </div>
    </div>
  </footer>
</main>

<style>
  :global(html) {
    transition: background-color 0.3s ease, color 0.3s ease;
  }

  :global(html.dark) {
    background-color: #000;
    color: #fff;
  }
</style>
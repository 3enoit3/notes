Interesting links
=================

Sources
* https://news.ycombinator.com/front

24/09/2024
* https://github.com/srush/GPU-Puzzles 1 thread per computation #gpu
* https://chipsandcheese.com/2024/09/22/intels-redwood-cove-baby-steps-are-still-steps/ Intel’s mobile strategy, moving away from the monolithic designs #cpu
* https://blogs.gentoo.org/mgorny/2024/09/23/overview-of-cross-architecture-portability-problems/ cross-architecture (int size) #crossplatform
* https://simonwillison.net/2024/Sep/18/board-of-the-python-software-foundation/ consistently contributed quality patches without extensive rewrites, you may qualify for commit privileges and become a core developer of Python #software
* https://www.fastly.com/ offer free bandwith to pyPI #python
  
23/09/2024
* https://simpleicons.org free svg for software products #blog
* http://www.mattmahoney.net/dc/text.html 200+ compression aglorithm compared: nncp / cmix first #compression
* https://blog.jim-nielsen.com/2024/sanding-ui/ "rub your hand on wood after sanding" with clicking everywhere in the UI #ui
* https://modern-json-schema.com/analyzing-the-openapi-tooling-ecosystem openapi pipeline: API (http parser -> data encoder -> data modeler -> report renderer) vs OAD #ai
* https://personal.sron.nl/~pault/#fig:scheme_light nice color set for black text #visualization
* https://www.nature.com/articles/d41586-024-02998-y local llm for privacy and tuning #ai
* https://www.theregister.com/2024/09/18/open_source_maintainers_underpaid/ 60% unpaid hobbyist, weight of security tasks increases, lack of turnover
  * industry security standards:
    * the NIST Secure Software Development Framework (SSDF)
    * the OpenSSF Scorecard -> highest awareness
    * the Supply Chain Levels for Software Artifacts (SLSA) Framework
    * the US Cybersecurity and Infrastructure Security Agency's (CISA) Secure by Design pledge.
* https://en.wikipedia.org/wiki/XZ_Utils_backdoor JiaT75 campaigned for three years to get co-maintainer position to sign off backdoor version #opensource
* https://socialcommunication.truman.edu/attitudes-emotions/social-initiation/ safe topic is the surrounding environment #social
* https://github.com/Telemaco019/kubesafe Mark one or more contexts as "safe" and define a list of commands that require confirmation before execution #safety
* https://github.com/rougier/scientific-visualization-book?tab=readme-ov-file Python + Matplotlib: color, ornaments, text #visualization
* https://raymii.org/s/software/Logging_all_Cpp_destructors_poor_mans_run-time_tracing.html trigger a SIGTRAP to debug with gdb + gcc run time instrumentation on all function and find destructor names #debug
* https://laike9m.com/blog/no-one-builds-in-public,160/ build in public: sharing your company’s story as it unfolds — with transparency, openness and vulnerability. #business
* https://keleshev.com/compiling-to-assembly-from-scratch/ #assembler
* https://classysoftware.io/chat-analysis/ hackernews sentiment analyzer #ai
* https://github.com/PeepDB-dev/peepdb command line to quickly inspect database tables without writing SQL queries #database
* https://github.com/cupy/cupy NumPy & SciPy for GPU #data
* https://github.com/commaai/openpilot operating system for robotics: give auto driving to cars #ai
* https://desosa.nl/projects/openpilot/2020/03/11/from-vision-to-architecture zeromq Pub-Sub for asynchronously communication in different language/platform/system + capnproto for encoding #software

20/09/2024
* https://github.com/dragostis/chili light parallelization in rust #rust
* https://github.com/MightyMoud/sidekick VPS Virtual Private Servers in cloud #network
* https://risk-engineering.org/concept/Rasmussen-practical-drift high complexity and tight coupling -> occasionally make large, unexpected “jumps” towards the boundary, when the organizational slack (buffering ability) is lower: operational slack “going solid” #risk
* https://text.makeup/#%2B #unicode
* https://arstechnica.com/gadgets/2024/09/real-time-linux-is-officially-part-of-the-kernel-after-decades-of-debate/ realtime patch in kernel #linux
* https://edolstra.github.io/pubs/phd-thesis.pdf Nix thesis #devops
* https://nix.dev/manual/nix/2.24/ each package has its own unique subdirectory + a hash of the package’s build dependency graph #devops
* https://ittavern.com/visual-guide-to-ssh-tunneling-and-port-forwarding/ #network
* https://wunkolo.github.io/post/2024/09/gpu-debug-scopes/ RAII in Rust with Drop trait #rust

19/09/2024
* https://github.com/rspeer/wordfreq/tree/master python frequent words in different languages #python
* https://github.com/exaloop/codon Python compiles to native machine code #python
* https://adam-mcdaniel.github.io/dune-website/ #shell
* https://github.com/adam-mcdaniel/atom #shell
* https://shikaan.github.io/assembly/x86/guide/2024/09/08/x86-64-introduction-hello.html assembler #hardware
* https://knhash.in/gentle-guide-to-self-hosting/ self hosting software #blog
* https://github.com/noperator/sol explain/edit one liner #shell
* https://medium.com/google-cloud/interning-in-go-4319ea635002 interning is
* https://en.wikipedia.org/wiki/Interning_(computer_science) re-using objects of equal value on-demand instead of creating new objects
* https://github.com/rabbitmq/rabbitmq-server/releases/tag/v4.0.1 AMQP 1.0 is now a core protocol #ipc

18/09/2024
* https://github.com/phiresky/ripgrep-all in PDFs, E-Books, Office documents, zip, tar.gz, etc. #tools
* https://www.graalvm.org/python/ python in java #python
* https://www.infinitepartitions.com/art001.html gzip format #compression
* https://github.com/voideditor/void open source copilot #ai
* https://gwern.net/book-writing in love with the idea of having published a book, but not with publishing #writing
  
17/09/2024
* https://github.com/satmihir/fair protect shared resources in go #go
* https://hurricanes2024.silurian.ai/#beryl/2024/07/02/0600Z/wind/surface/level/overlay=off/orthographic=-7.37,41.19,3000 weather simulation #misc
* https://mango.pdf.zone/i-give-you-feedback-on-your-blog-post-draft-but-you-dont-send-it-to-me "The title gets read way more than the rest" + "Use more examples" #writing
* https://news.ycombinator.com/item?id=41519046 "ping goodhost | sed -e 's/.*/ping/' | vocoder" he wandered through the building wiggling Ethernet connectors until the sound stopped #software
* https://arcan-fe.com/2016/12/29/chasing-the-dream-of-a-terminal-free-cli/ command-line appl without restrictions of normal (terminal-emulator + sHell + application) #shell
* https://ppml.dev/index.html in machine learning, https://www.jjinux.com/2015/07/the-waterfall-model-was-straw-man.htmltreat data as code (including tech debt) #ai
* https://www.jjinux.com/2015/07/the-waterfall-model-was-straw-man.html Royce’s 1970 paper credited with “inventing” the waterfall model, actually to criticize it -> no one ever wrote a book that proposed it was a good model #software
* https://franzelio.franzai.com/ draw lines to play music #misc
* https://whattrainisitnow.com/ firefox 4 trains (Extended Support Release, release, beta, nightly) #software

16/09/2024
* https://www.techradar.com/news/ai-is-going-to-ruin-humanity-just-not-in-the-way-you-might-expect Google can make us smarter – ChatGPT won’t #ai
* https://www.msn.com/en-gb/money/technology/we-re-witnessing-the-death-of-the-graphics-card-in-real-time-right-now-and-i-couldn-t-be-happier-about-it/ar-AA1qCttQ focus on ai instead of gamers #ai
* https://simonwillison.net/2024/Sep/15/how-to-succeed-in-mrbeast-production/ C-Players are just average employees. […] They arn’t obsessive and learning #leadership
* https://cs.pomona.edu/classes/cs181g/ game and rust #rust
* https://peterszasz.com/how-to-lead-your-team-when-the-house-is-on-fire/ "Bias heavily toward action" + "Conducting regular architecture reviews to spot and address emerging issues" #leadership
* https://newsletter.pragmaticengineer.com/p/paying-down-tech-debt It’s harder to read code than to write it #software
* https://newsletter.pragmaticengineer.com/p/zirp-software-engineers end of zero interest rate policy (ZIRP) by central banks: pressure to achieve profitability, less venture capital funding, Big Tech getting bigger #economy
* https://www.implicitcad.org/ cad with code #misc
* https://lwn.net/Articles/990307/ 6.11 linux kernel: write to busy executable files, block drivers in Rust #os
* https://www.raylib.com/ simple game engine #game
* https://github.com/phil-opp/blog_os os in rust #rust
* https://blog.yoshuawuyts.com/nesting-allocators/ nested rust allocators #rust
  
13/09/2024
* https://www.youtube.com/watch?v=J_EehoXLbIU simple eBFP #debug
* https://www.usenix.org/conference/srecon23apac/presentation/liang real eBFP debugging #debug
* https://github.com/keisku/gmon monitoring go with eBFP #debug
* https://blog.spiraldb.com/compressing-strings-with-fsst/ compression in rust #rust
* https://duckdb.org/2022/10/28/lightweight-compression.html lightweight compression vs general #compression
* https://fight-flash-fraud.readthedocs.io/en/latest/introduction.html test flash card #hardware
* https://jina.ai/news/reader-lm-small-language-models-for-cleaning-and-converting-html-to-markdown clear web content #ai
* https://github.com/mozilla/readability api to remove non readable content (header..) #web
* https://rfd.shared.oxide.computer/rfd/0026 os review for virtualization (qemu risk, systemd risk) #os
* https://larahogan.me/blog/be-a-thermostat-not-a-thermometer/ prevent over reaction to propagate (thermometers) by setting the room temperature (thermostat) #scrum
* https://www.gtf.io/musings/why-haskell "A language that doesn’t affect the way you think about programming is not worth knowing. ~ Perlisism" #haskell

12/09/2024
* https://herbertlui.net/david-chang-on-the-long-hard-stupid-way/ teach someone to better themselves through their own personal integrity #software
* https://gist.github.com/thoughtpolice/9c45287550a56b2047c6311fbadebed2 interdiff review (multiple commits) #git
* https://netflixtechblog.com/noisy-neighbor-detection-with-ebpf-64b1f4b3bbdd ebpf overload #debug
* https://coredumped.dev/2024/09/09/what-is-the-best-pointer-tagging-method/ encoding information in pointer values #cpp
* https://eugeneyan.com/writing/web-frameworks/ FastHTML Next.js SvelteKit #web
* https://www.16elt.com/2024/09/07/future-proof-code/ How can I make it flexible without going overboard? #software
* https://thesambarnes.com/leadership/gripes-go-up-not-down-a-leadership-lesson/ There’s a chain of command: gripes go up, not down #lead

11/09/2024
* https://antithesis.com/blog/multiverse_debugging/ debug by coming back 5s before the issue "Multiverse debugging" #debug
* https://tech.marksblogg.com/extracting-osm-features.html geograhic database #ai
* https://arxiv.org/abs/2403.18103 Tutorial on Diffusion Models for Imaging and Vision (math theory) #ai
* https://en.wikipedia.org/wiki/Floral_formula notation for flower shapes #misc
* https://github.com/dbcli/litecli nice sqlite client #database
* https://buttondown.com/hillelwayne/archive/3866bd6e-22c3-4098-92ef-4d47ef287ed8 comments #software
* https://buttondown.com/hillelwayne/archive/why-not-comments/ negative comment (why not) to explain trade off #software

10/09/2024
* https://dl.acm.org/doi/10.1145/3589334.3645323 QUIC protocol optimized for TCP webapplication https://en.wikipedia.org/wiki/QUIC #network
* https://blog.gitbutler.com/why-github-actually-won/ GitHub won because it started at the right time and it had good taste #git #business
* https://avestura.dev/blog/creating-a-git-commit-the-hard-way git internals #git
* https://blogsystem5.substack.com/p/windows-nt-vs-unix-design #os
* https://fennel-lang.org/ lua + lisp #script
* https://github.com/josephburnett/jd json diff #json
* https://tookmund.com/2024/09/hibernation-preparation #linux
* https://hnbooks.pieterma.es/ books #misc #ai
* https://hdbscan.readthedocs.io/en/latest/ clustering of books in https://hnbooks.pieterma.es/ #ai
* https://openlayers.org/ layers on maps #visualization

09/09/2024
* https://misinforeview.hks.harvard.edu/article/gpt-fabricated-scientific-papers-on-google-scholar-key-features-spread-and-implications-for-preempting-evidence-manipulation/ #ai
* https://bernsteinbear.com/blog/fenster-microui/ small ui + small wm #ui
* https://blog.trailofbits.com/2024/09/06/unstripping-binaries-restoring-debugging-information-in-gdb-with-pwndbg/ plugin for gdb with binary ninja #debug
* https://conspirator0.substack.com/p/baiting-the-bot python code for ai in local #ai
* https://luajit.org/luajit.html embedded lua just in time #script
* https://reclaim-the-stack.com/docs/kubernetes-platform/introduction open source implementation #kubernetes
* https://www.humprog.org/~stephen/blog/2024/08/27/#how-to-wrap-cc-really hack into gcc #gcc
* https://github.com/weinberg/SQLToy/wiki/Two-Key-Concepts sql implementation details #db
* https://www.brightball.com/articles/story-points-are-pointless-measure-queues queues over story points #scrum

11/07/2024
* https://github.com/lm-sys/RouteLLM select best model (cheap and low quality or expensive and high) depending on the query #ai
* https://zed.dev/linux zed modern editor #ide
* https://www.timdbg.com/posts/useless-x86-trivia/ #x86
* https://santhoshsundar.medium.com/using-the-5s-principle-in-coding-6237a1614a02  Sort, Set in Order, Shine, Standardize, and Sustain. #software
* https://garrettdbates.com/blog/software-architecture/why-use-onion-layering onion #architecture

20/06/2024
* https://3tilley.github.io/posts/simple-ipc-ping-pong/ ipc udp/tcp vs shared memory #rust
* https://ludic.mataroa.blog/blog/i-will-fucking-piledrive-you-if-you-mention-ai-again/ #ai 

23/05/2024
* https://amber-lang.com/ compiled as bash #shell

22/05/2024
* https://matthewstrom.com/writing/ui-density/ #ui
* https://swtch.com/%7Ersc/regexp/regexp1.html #regex
* https://breckyunits.com/scrollsets.html knowledge storing as text #db

18/03/2024
* https://www.sheshbabu.com/posts/thoughts-on-the-future-of-software-development/

13/01/2024
* https://nautil.us/the-magic-of-the-blackboard-487759/ the writing, the relay, and the rethink #softskills
* https://github.com/aspen-cloud/triplit “full stack database” #db
* https://rkyv.org/motivation.html directly referencing bytes in the serialized form #rust

09/01/2024
* https://ggnotes.com/the-best-way-to-get-unstuck the way to escape stuckness is by taking action. #softskills
* https://ggnotes.com/40-for-40---wisdom-i-want-to-remember Lead when nobody else wants to. #misc
* https://medium.com/@ameet/strong-opinions-weakly-held-a-framework-for-thinking-6530d417e364 I will force myself to make a tentative forecast based on the information available, and then systematically tear it apart #softskills
* https://blog.glowforge.com/strong-opinions-loosely-held-might-be-the-worst-idea-in-tech/ The loudest, most bombastic engineer states their case with certainty, and that shuts down discussion #softskills
* https://newsletter.pnote.eu/p/simple-lasts-longer use browser cache instead of server #software
* https://tonybaloney.github.io/posts/python-gets-a-jit.html JIT compiler, is a compiler that emits machine code #python

04/01/2024
* https://www.ricmedia.com/tutorials/build-a-raspberry-pi-nas-server#usb-flash raid 1 on raspberry pi #tools
* https://github.com/tldraw/tldraw miro equivalent self hosted #tools
* https://liveplusplus.tech/ live c++ update and results #cpp #tools
* https://github.com/ktock/container2wasm #wasm
* https://wozniak.ca/blog/2024/01/02/1/index.html gcc is a driver, not a compiler #cpp
* https://github.com/uutils/coreutils #rust
* https://blog.vmsplice.net/2024/01/qemu-aiocontext-removal-and-how-it-was.html #multithread
* https://blog.lenot.re/a/introduction kernel in rust (30% of system calls) #rust

Xmas break
* https://pdx.su/blog/2023-10-25-css-is-fun-again/ modern css with preprocessor nesting and color-mix #css
* https://suggestions.ink/ text suggestion protocol #tools
* https://sprocketfox.io/xssfox/2021/12/02/xrandr/ best way to use big screen is to tilt 22 degree
* https://www.paradigm.xyz/2020/08/ethereum-is-a-dark-forest sneaky recovering not to be spotted by bots #blockchain
* https://nick.scialli.me/blog/why-im-skeptical-of-low-code/ 80% can be done, but 20% needs custom #software
* https://techbooks.substack.com/p/why-asking-your-customers-what-they focus on the job to be done, pay attention to workarounds (spent effort to work around) #business
* https://simonwillison.net/2023/Dec/31/ai-in-2023/ Code may be the best application #ai
* https://chhopsky.itch.io/an-easy-fix a game about fixing a jira ticket #game
* https://rnikhil.com/2023/12/31/ai-cfr-solver-poker.html ai on poker #ai #game
* https://matklad.github.io/2023/12/31/git-things.html not rocket science rule: all tests green + new test to accept PR #git
* https://www.inc.com/jeff-haden/27-years-ago-steve-jobs-said-best-employees-focus-on-content-not-process-workplace-research-shows-he-was-right.html focus on content (outcome), not process - get things done - take care of superstars #business
* https://garymarcus.substack.com/p/things-are-about-to-get-a-lot-worse copyright are easily broken: "animated sponge" #ai
* https://fernandovillalba.substack.com/p/its-not-microservice-or-monolith team cognitive load capacity (one vs many) #architecture
* https://lwn.net/Articles/955376/ the linux graphic stack #linux #architecture
* https://ieeexplore.ieee.org/document/10372494 process quality (reviews/flakiness) -> code quality (readability/testability) -> system quality (defects/perf) -> product quality (usability/revenue); cyclomatic complexity a poor proxy of code quality #software
* https://cacm.acm.org/magazines/2024/1/278891-10-things-software-developers-should-learn-about-learning/fulltext Experts Recognize, Beginners Reason #learning

23/11/2023
* https://jvns.ca/blog/2023/11/23/branches-intuition-reality/ git lets you do rebases “backwards” #git
* https://catern.com/services.html By avoiding the maintenance and upgrade costs of a service, a library can afford to contain more functionality #services
* https://lwn.net/SubscriberLink/952029/412bfd44912e90b2/ Whether the kernel community has truly concluded that it is committed to Rust remains to be seen #rust
* https://gbdev.io/pandocs/ most comprehensive technical reference to Game Boy #game
* https://github.com/visioncortex/vtracer open source software to convert raster images (like jpg & png) into vector graphics (svg) #svg
* https://hakaimagazine.com/videos-visuals/the-secret-language-of-ships/
* https://ln.hixie.ch/?start=1700627373&count=1 problems with Google today stem from a lack of visionary leadership, "Decisions went from being made for the benefit of users, to the benefit of Google, to the benefit of whoever was making the decision. Transparency evaporated" #vision
* https://www.timdbg.com/posts/writing-a-debugger-from-scratch-part-1/ debugger in rust, from Microsoft Debugger Platform team member #rust

22/11/2023
* https://rocket.rs/ webserver with nice json implementation #rust
* https://rachit.pl/files/pubs/filament.pdf formalization of electronics #electronic
* https://mastersofmedia.hum.uva.nl/blog/2019/03/26/can-we-deter-tech-monopolies-and-combat-income-inequality-through-a-reformed-open-source-software/ #opensource
* https://www.wsj.com/articles/nasa-james-webb-space-telescope-greg-robinson-images-11657137487 marginal improvements #software

* https://www.reddit.com/r/spacex/comments/gxb7j1/we_are_the_spacex_software_team_ask_us_anything/
  
20/11/2023
* https://www.evanjones.ca/setenv-is-not-thread-safe.html setenv() and getenv() on different threads can crash #thread
* https://codemanship.wordpress.com/2023/11/20/the-bluffers-guide-to-the-mythical-man-month/ Value of Iteration: "software should be developed in stages, with each stage building on the previous one"; "Achieving conceptual integrity often involves a strong guiding hand, such as a chief architect" #software
* https://www.vox.com/future-perfect/23965898/child-poverty-expanded-child-tax-credit-economy-welfare-phase-ins #misc
* https://github.com/bitswired/rustgpt "the Axum framework combined with HTMX, providing a Rusty web development experience" + sqlite #rust
* https://www.scu.edu/ethics/focus-areas/business-ethics/resources/seven-signs-of-ethical-collapse/ keep costs low; keep quality high; focus on customer service #business; We’re dependent on individuals saying, ‘No, we can’t do that,’ #business
* https://sourcegraph.com/blog/zoekt-creating-internal-tools-at-google Taking the bull by the horns #tools
* https://blog.matiaspan.dev/posts/exploring-dagger-streamlining-ci-cd-pipelines-with-code/ Dagger is a new tool that promises to fix the yaml and custom scripts mess that CI/CD currently is by building pipelines as code #devops


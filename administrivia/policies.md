# Policies

## Academic Integrity

You are encouraged to study and discuss topics together. For most assignments you are expected to do the actual coding, math, or writing on your own; for others (which will be clearly identified) you will work as part of a team. When in doubt, mention any people or other sources who helped you.

Remember that *the point of assignments is to help you learn*. This practice and the feedback you receive are vital for you to learn to solve problems in, and communicate about, the subject; you will need these skills in later courses and in life after college. The assignments are not there to supply the instructor with an additional copy of the answers. Turning in plagiarized work is a waste of everyone's time.

You can find detailed policies in the College's [Statement on Academic Integrity](https://docs.lclark.edu/undergraduate/policiesprocedures/academicintegrity/) and in sections [VIII (Outcomes)](https://college.lclark.edu/student_life/-our-departments-/student-rights-responsibilities/student-code-of-conduct/#VIII) and [XVII (College Honor Board Hearing Procedures)](https://college.lclark.edu/student_life/-our-departments-/student-rights-responsibilities/student-code-of-conduct/#XVII) of the Student Code of Conduct.

### Generative AI

Large language models like ChatGPT and Copilot are surprisingly effective at solving *easy* programming problems, as they have been trained on many solutions to such problems. They fail on more challenging problems, because they don't have an internal model of what they're talking about; they are simply, in the words of Rumman Chowdhury, "spicy autocorrect".

It is therefore essential that you don't use an LLM to solve your assignments. Without practicing the skills these assignments are meant to teach, you will eventually reach problems that neither the LLM nor you can solve; worse, you will reach problems for which the LLM produces code that is subtly incorrect, inefficient, or insecure, and you won't have sufficient understanding to notice or fix the problem.

All of that said, LLMs are used widely by professional programmers. They are quite handy when you understand the relevant concepts but just don't know the syntax or which library functions to call. It may be that having a computer write the boilerplate code can free you up to think about overall system design, testing, and other higher-level issues. I will experiment with this in some upper-level courses, but **you may not use an LLM to generate code except where it is explicitly allowed**.

I remain wary that LLMs use vastly more energy than traditional web searches, have often been trained on data that were arguably stolen, and are [unlikely to remain free once we've become dependent on them](https://en.wikipedia.org/wiki/Enshittification).

## Assignments

### Handing In Assignments

Assignments are handed in through Google Classroom. If you have trouble with the handin system, talk to me or a teaching assistant as soon as possible to get things straightened out.

### Ungrading

The book *[Ungrading](https://wvupressonline.com/ungrading)*, edited by Susan Blum, makes a strong case that grades are counterproductive:

* Grades encourage thinking about *how well* you are doing instead of *what* you are doing.
* Grades do not provide effective feedback.
* Grades encourage competitiveness over collaboration.
* Grades encourage gaming the system and even cheating.
* Grades can be arbitrary and subjective.
* Grading systems can be needlessly complicated.
* Grades cause massive stress for students and instructors.
* Grades emphasize control and hierarchy over learning and trust.
* Grades are not a good predictor of future success.

In light of this, I have joined the growing movement of faculty who do not rely on grades. Instead, I will give you extensive feedback on your work. You can focus on learning rather than on jumping through hoops.

Your feedback for each assignment will include one of the following emoji:

⭐️	Above and beyond; did optional challenge problems, code is particularly clean, etc.  
✅	Complete, passes all tests; this should be the most common "grade"  
👣	Started; made some nontrivial effort and handed something in  
❌	Nothing handed in

I do still have to submit grades at the end of the semester. To that end (and, more importantly, to increase communication), we will discuss your progress (in person or in writing) several times over the course of the semester. In these conferences and self-assessments, you will tell me (among other things) [what grade you deserve](https://docs.google.com/document/d/1xXvmiHJB66jHNd4ZFUIw1FyP-7K8a1wr882bVuA3naM/edit?usp=sharing). I reserve the right to override you if you are being far too easy or (more likely) far too hard on yourself, but this is uncommon.

It is also vital that you do the work. If you fall behind, you won't be ready for more challenging material later in the course, in your college career, and in life. I cannot in good conscience allow you to pass a class in which you have barely participated. To ensure that you are keeping up, you must turn in (on time, with the slack given by the late policy described below) at least half of the course assignments to earn a D. Students who cannot meet this very low threshold are almost certainly struggling with external issues such as physical or mental health; if you are in such a situtation, it is vital for you to get help before the problem becomes catastrophic. 

### Late Policy

I have several goals in setting a late policy:

* Encourage you to do the work, because practice is where the learning really happens. Earlier assignments prepare you for later ones.
* Help you manage your time and prevent you from getting hopelessly behind.
* Minimize the amount of stress you experience when you do run up against a deadline. I understand that illnesses, athletic events, technical difficulties, and so on sometimes lead to handing in things late.
* Be able to give feedback on everyone's submission to a given assignment at the same time, for efficiency and consistency. 
* Avoid having to waste my time looking at handin dates, listening to requests for extensions, etc.
* Have a reasonable point after which I can discuss the assignment in class without giving away the answer to people who haven't done it yet.

Each assignment therefore has a due date (when you should turn it in) and a **_one-week grace period_**. Outside of *extreme* circumstances, you can't turn things in after the grace period.

Some time (hopefully a couple of days) after the due date, I (or a teaching assistant) will give feedback on the assignment. If you still have time before the grace period, you may hand in a revised version. After the grace period ends, we will give feedback again. If you want to talk about additional revisions, or an assignment that you came back to much later, come by lab/office hours.

| Your Excuse for Missing the Grace Period Deadline | What I'll Say |
| --- | --- |
| I was sick for a couple of days. | Sorry, but it's already a week late. |
| My laptop died. | Sorry, but it's already a week late. |
| I had to participate in an athletic event or concert. | Sorry, but it's already a week late. |
| I had to drive my roommate to the hospital. | Sorry, but it's already a week late. |
| My cat died. | I'm very sorry, but it's already a week late. |
| I have special accommodations from Student Support Services. | If the one-week grace period is not sufficient, come talk to me *before* the due date. |
| I was attacked by a llama and I've been in the hospital for a week. | Come talk to me. |
| I was attacked by two llamas and I've been in the hospital for two months. | You should probably withdraw for the semester. |

Do not misinterpret the grace period as the "real" deadline. The deadline is the deadline; the grace period is for unusual circumstances.

**_The last day of regular class (*not* the final exam period) at 11:59 PM (my clock, not yours) is an absolute final deadline after which no assignments will be accepted._**


### Programming Assignments

A program should:
- Compile and run.
- Use exactly the names specified for classes, methods, etc. This both makes my grading easier and is good practice for the inevitable day when you’re working on a large project with many other programmers.
- Behave as specified (e.g., pass all tests).
- Use appropriate data structures and algorithms.
- Have an interface devoid of spelling and grammatical errors and graphical glitches.
- Clearly present the information the user needs to make decisions and allow the user to easily communicate those decisions back to the program. While it can be very useful during debugging to print some additional information (e.g., about the state of data structures), the final version of a program should not do this.
- Have elegant, clear, well-commented code. Any commented-out code should be removed.
- Behave reasonably even in situations not explicitly tested.

Except where specified, you do not need to do error-checking in programs. For example, if you ask the user to type an integer, you may assume that they will do so, and are not responsible for what happens if they type “fnord” instead.

### Writing Assignments

In general, a paper should:
- Use complete sentences and be devoid of spelling, grammatical, and typographical errors.
- Be well-organized. Similar thoughts should be grouped together. The document should have a purpose; every element should support this purpose.
- Provide evidence for claims. In a research paper, this evidence should include proper citations. Just about any citation format is acceptable, as long as it is consistent; a good choice for computer science is [IEEE style](https://ieeeauthorcenter.ieee.org/wp-content/uploads/IEEE-Reference-Guide.pdf). Tools like [Zotero](https://www.zotero.org/) can make citing sources vastly less tedious.
- Have something important to say. The very best papers change the reader's thinking about the topic.
- Omit needless words. Language should communicate rather than getting in the way.
- Be single-spaced. Other instructors' preferences may vary, but I believe double-spacing is a relic of the days when feedback was written on paper.

### Mathematical Assignments

Mathematical assignments (both exercises and proofs) are very similar to writing assignments. Acceptable formats include OpenDocument (.odt), Word (.docx), and PDF; ask in advance if you want to use something more exotic. You must learn to use LaTeX or the equation editor in your word processor.

A mathematical paper should:

- Be correct.
- Be clearly explained, using appropriate notation, prose, and diagrams.
- Address special and boundary cases.

## Disabilities
If you have a disability that may impact your academic performance, you may request accommodations by submitting documentation to the [Office of Student Accesibility](https://www.lclark.edu/offices/student-accessibility/). After you have submitted documentation and filled out paperwork for the current semester requesting accommodations, staff in that office will notify me of the accommodations for which you are eligible.

## Sexual Misconduct

Our school is committed to fostering a safe, productive learning environment. Title IX and our school policy prohibits discrimination on the basis of sex. Sexual misconduct — including harassment, domestic and dating violence, sexual assault, and stalking — is also prohibited at our school.

Our school encourages anyone experiencing sexual misconduct to talk to someone about what happened, so they can get the support they need and our school can respond appropriately.

If you wish to speak confidentially about an incident of sexual misconduct, want more information about filing a report, or have questions about school policies and procedures, please contact our [Title IX Coordinator](https://www.lclark.edu/about/title_ix_compliance/).
Our school is legally obligated to investigate reports of sexual misconduct, and therefore it cannot guarantee the confidentiality of a report, but it will consider a request for confidentiality and respect it to the extent possible.

As a teacher, I am also required by our school to report incidents of sexual misconduct and thus cannot guarantee confidentiality. I must provide our Title IX coordinator with relevant details such as the names of those involved in the incident.

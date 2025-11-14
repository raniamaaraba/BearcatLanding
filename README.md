# BearcatLanding
As a part of UC's UI course--we are redesigning a 'bad' user interface in which we decided on the UC landing portal page
## Live Deployment: https://bearcatlanding.netlify.app/
Re-worked by Rania Maaraba and Meredith Bartel

Installed Packages: 
npm
postcss
tailwing config

Why the landing page? A great article to figure out why (other than it being not personal to students needs) check out this article by Harry Albert at The Williams Record. 
https://williamsrecord.com/463148/opinions/listen-i-dont-like-to-complain-but-why-are-the-colleges-websites-so-painful-to-use/ 

Albert makes a great point that a lot of these websites look like they were created during the beginning of the Dot Com Bubble and have not been updated since! Although the UC's landing page 
has been updated--it is still clunky with its organisation and moderate cleanliness. Most colleges spend absorbant amounts of money to run and host these pages to make sure they are secure 
and functional for the students--but at what cost for the user? Is the college truly spending their money in the best way if the user cannot properly navigate the pages?

GeeksforGeeks has a great article on why UI is important. See it at https://www.geeksforgeeks.org/websites-apps/importance-of-ui-ux-design/
As well as the company that hosts the UC page, Modo, claims that their product improves work time (time being lost to not understanding applications), millions of dollars saved from
being lost in prodoctivity, and absorbant ROIs. Both GeeksforGeeks and Modo get this both right--having a page with good UI saves the user not only from headaches but gains trust in the user
as well as the company. This saves a lot of confusion for students to ask professors or IT staff that may not understand what they are asking or why they do not get what they are doing. 
Making sure that a UI is easy to read, intuitive can save a lot of time and money for both the college and for its students.

Current Issues:
-There is lots of redundency, same actions 2-3 times on the same page
-Extra buttons that are often highlighted as 'useful' or 'quick access' but takes up more space on the page
-Does not highlight the important features that one would quick need to access ie canvas, catalyst (our scheduling system), and so on

This is the starting landing page--highlighting finances, daily schedule, among many buttons that simply go unused with a lot of wasted space
<img width="1512" height="749" alt="Screenshot 2025-10-29 at 20 26 39" src="https://github.com/user-attachments/assets/7e862258-a918-49a5-88f1-669e76c1e7e8" />

A hamburger menu in which I have never used before! Lots and lots of more features highlighting the same information we saw previously on the landing page
<img width="579" height="750" alt="Screenshot 2025-10-29 at 20 30 50" src="https://github.com/user-attachments/assets/d425d9b0-b7a4-49df-b7ed-0965da2a43d4" />

Side menu which I needed to show--these features aren't even implemented! They are simply buttons to external links
<img width="429" height="530" alt="Screenshot 2025-10-29 at 20 33 31" src="https://github.com/user-attachments/assets/758b745a-69f9-4d69-903f-832b4e23a3fc" />

Finally, the bottom and the only critical section of the page. Ask any UC student and 98% of the time they will say they scoll to the bottom of the page to access these features
<img width="1512" height="752" alt="Screenshot 2025-10-29 at 20 34 17" src="https://github.com/user-attachments/assets/fd8ec4c0-dba6-425c-af7c-4f00c3f01539" />

Some things we want to do:
-Highlight Canvas, Catalyst, and some of the other features at the bottom of the page and move them up
-Make tabs for Schedule, main page, and finances
-Re work the hamburger menu for better information (pertaining to the college of engineering in this example but more college based as well as your ciriculum)
-Group buttons by common points wheter it be the type of resouce, when it is typically used, something to mesh everything together
-Use your Canvas picture (if any) rather than your Bearcat ID picture which tramatised many of their freshman selves

Initial Sketch of Landing Page:
<img width="1029" height="641" alt="Screenshot 2025-10-29 at 21 04 45" src="https://github.com/user-attachments/assets/8271ac0e-461e-4481-bf21-ffd6dce026fe" />

-Keeps the same feel as it is now
-Highlights the features we need most
-Leaves space for it to be modified

# Final Production
Fancy a walkthrough? Check out our video here! 
https://vimeo.com/1136971881?share=copy&fl=sv&fe=ci#t=0

## Main Dashboard 
<img width="1502" height="753" alt="Screenshot 2025-11-14 at 11 37 03" src="https://github.com/user-attachments/assets/3f06f5b1-2156-4698-947a-fb06d8437fb7" />
Our new dashboard encompasses as many as our desired features as we could fit! As seen in our video--pretty much all of the links you see on the Quick Access as well as on the sidebar as completely functional! (except for my grad plan since that is nested within another website we could not obtain) Typically, you have to navigate to several pages just to see some of your most critical information that we are highlighting at the top--such as your GPA and Degree Applicable Credits (very important for CCP and AP test takers!) Although slightly cut off in this view is today's schedule is up-front and in-your-face to make sure you stay on top of your game!

<img width="1512" height="750" alt="Screenshot 2025-11-14 at 11 37 11" src="https://github.com/user-attachments/assets/eeb80b8f-abc2-4723-bebe-1abdb377cd41" />
Scrolling down a bit further--we can see our current courses and their next due assignments. This acts almost as an additional reminder to that of the course stream in Canvas but is a great reminder to keep you up to date on assignments without navigating to Canvas. Want to check out the full assignment? Super easy! Just Click the 'View in Canvas' button (*note this is a general Canvas link for our purposes). We also have information on the right-hand side about Campus Resources and various times of locations. Most of the time--if you are not consistently going to a location on campus or are taking the shuttles daily (although seeing when the next one arrives is also critical even if you do) when facilities are closing on campus. Due to several events or football games--these times can vary without you realising it and makes it convenient to look on the side rather than to navigate to UC's Campus Life page then to Food then to Food Courts then to your desired food court hours just to see that OTG actually closed 30 minutes ago from running out of cooking materials! Right below this, we also have the Bearcat Dollars balance that allows you to see how much money you have on your Bearcat Card to spend at nearby Cincy Deli for a replacement sandwich for dinner as well as add additional funds if you run out of cash for a tip!

## Finances
<img width="1511" height="746" alt="Screenshot 2025-11-14 at 11 37 21" src="https://github.com/user-attachments/assets/74b39ec1-693e-4aa3-a5d8-6e174bfa584d" />
Digging deeper into our finances tab--this is were majority of your tuition payments as well as additional information on your Bearcat Dollars can be found. One thing I often notice with my tuition in the original UC Dashboard is are incorrect totals being displayed if you make a partial payment or have scholarships being applied. There is also quick and easy access for navigation for the breakdown of the semester (this typically takes up to a minute to load on UC's!) so you can see where every penny is (mostly) going. You can also get up-to-date information on scholarships and FASFA loans. 

<img width="1512" height="750" alt="Screenshot 2025-11-14 at 11 37 11" src="https://github.com/user-attachments/assets/9a96b4ae-8010-46d4-8eb9-6c188399f209" />
Additionally, scrolling further down gives you a more in-depth look into your payment history for both tuition and Bearcat Dollars. Did Mom and Dad send you $200.00 for the semester and now you only have $13.00 left? Oops, at least I can see what I spent it on! Issues with funds bouncing back and not paying your tuition properly? Confirm that it went through in your payment history!

## Schedule
<img width="1512" height="763" alt="Screenshot 2025-11-14 at 11 37 40" src="https://github.com/user-attachments/assets/bfce2a48-4260-432b-a0f2-fa4d9c708911" />
As a certified lover of the Canvas Calendar--this is pretty reminiscent of the addition of displaying your weekly classes in addition to your assignments. This is great for those who are trying to figure out if they can attend club meetings posted on their calendar but accidentally see that they have a midterm project due at 11:59!! You can easily as well flip through last month and next month to figure out plans and schedules. 

Final Limitations of the Project:
There are two main features that are currently not working/ were not implemented due to scope purposes and this just being a re-make of the university portal. Many include the finance features (adding more money to your account, viewing specifics about finances and your schedule) and well as the search feature. Ideally--this would be a catch all search funciton for things like a directory, all previously implemented features, and any other UC websites such as My Bearcat Network. There is additionally currently no feature to modify events on the calendar or click on them for descriptions of the event / homework. 

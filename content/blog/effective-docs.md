+++
title="Create effective project documentation"
date=2024-01-27
draft=true
[taxonomies]
tags=["essay"]
+++

I've learned a lot about creating effective project documentation.
Special care must be taken to make sure intranets, wikis, are outdated, incorrect, or unneeded.
People must resort to contacting relevant team members for information.
This makes work slower and more importantly may lead to errors in expectation.
Even worse when teams are smaller!

How do we get knowledge out of the heads of project members and into a space?

There are no set guidelines for writing documentation a lot of the time like in coding.
Where there are standards, guidelines, and frameworks.

Here is what I try to follow.

## Developing a culture

Most importantly, your team needs a _culture_ of writing documentation.
This means a single source of truth with notes that have _ownership_ and change tracking (dates, authorship)
Anyone sometime asks you a question, you should first check the documentation for that.
Update it, and use it as a direct response to the question.
Finally, ask for feedback on how to fix it.
This may be called read-through documentation or caching, and it works well to have continuously-updated comprehensive documentation that actually solves problems. 

This is noticeably present during onboarding.
Generate drafts for missing content by having new team members write them as they get up to speed, and have them reviewed by a senior team member.

Whenever possible, docs should be integrated into your workflow.
This means placing docs right into docstrings and having them build, or integrated into PRs.
However, take care that you have three sources of knowledge.
Automation is also a good thing TM.

1. Specific: API and usability, right in the docstrings
2. _USAGE_!!!: How your API is intended to be used, combinations of functions, etc.
3. Best practices and stylistic concerns.

If new code is created and missing documentation, PR is not approved.
Enforcing this rule is the job of management and culture.

## Anticipate your audiences

Docs are written to _share information_ with people.
That's why it's important to identify and group your audience.
Different people, like marketing or developers, need docs tailored to their needs.
For this reason too, your documentation system should be accessible to people of all skill levels.
It should be automated single source of truth but with multiple points of access.
It should have commit diffs with your code such that the docs grow as the code grows but old revisions for older versions are still accessible..

For developers, project documentation is also important.
Approaches tried and why we're not doing it.

Have a way to search version history and full-text search /fuzzy matching for easy access.
Tags are better than folders.

The more general concept behind that is called document life cycle. Ideally you would want to have different possible status, like draft, published, verified, outdated, archived. Most wiki tools don't handle that well. And make outdated = archived which is an issue as in your case, will not work, and outdated documents will keep polluting your knowledge base.

Can 

I used this approach when doing the DevRel for Chrome DevTools. I would browse Stack Overflow for uses cases not explained in the docs, add a doc for it, and then link my Stack Overflow answer to the (newly created) official doc.
Semaphor • on Feb 17, 2022
That is a great idea. We have a company-wide OneNote notebook with some (extremely) rudimentary documentation, I hope I’ll remember this the next time someone asks me a question, so I can add it there :)
100011_100001 • on Feb 17, 2022
Where is the documentation stored? One of my main blocks is how hard it is to update documentation.
bluGill • on Feb 17, 2022
Where is just a tool, don't get too locked into a tool just get one and use it. The important part is that IT will agree to move move your URLs around every few months.
100011_100001 • on Feb 17, 2022
Interesting. For me it's a problem of speed. How fast can I find it, and how fast I can edit it.
I rely on git repos using markdown because it's fast and I can search, however things like tables etc can get annoyingly complex to upkeep.
phphphphp • on Feb 17, 2022
I've not tried this at scale so it remains theory for me, but at a previous company, I proposed that we tackle this problem in the same way medical literature is managed by health organisations. That is, every page is owned and every page has an expiry: when a page expires, the owners are obligated to review it. The "yikes" part of that idea is that it feels burdensome, but that's because retaining and managing knowledge is burdensome and businesses should be measuring knowledge as an asset (or liability) and budgeting accordingly.
Ultimately, most people are digital maximalists when they'd be better off being digital minimalists. I (in my personal life and in the small teams I work with) purposefully delete things that I do not wish to accept the burden of owning. Either something is important enough to justify the burden of ensuring it's accurate, or it isn't and it is deleted.

I have found that thinking about documentation in these terms, it becomes clear what to document and what not to document, and it forces better practices elsewhere in the business -- like writing code that clearly communicates the why, or designing business processes that leverage a core set of business information.
kaycebasques • on Feb 17, 2022
As a technical writer of 9+ years I can share some concrete experience related to your theory. The theory is right on the money. Assigning an owner and tracking last review date is a very effective practice. Google had a great system (go/fresh-source) in their internal doc infrastructure, g3doc. I learned recently that parts of Microsoft have a similar setup. You put an "owner" field in the YAML frontmatter of your doc (the value is the username of the person who owns the doc), as well as a "last review" field (value is last review date). Then you build a reporting system that tracks who is keeping their docs up-to-date and who is not. You can ensure that people don't game it (e.g. just updating the "last review" field without actually looking at the docs) by cross-referencing with other metrics, such as number of bugs opened that are related to that area of the docs.
bobbydreamer • on Feb 20, 2022
Yep. The same approach my org uses as well. There is a team, who deals with all orgs docs maintain it. There is a internal portal to submit and you start getting mails 2 months before expiry.
Respective team meetings, it's a agenda to talk about what needs to be updated, after updating a draft will be sent and later uploaded in the portal.
WJW • on Feb 17, 2022
I think that expiry of documentation is a great idea, but it could go further:
- Often, teams "own" stuff but the real knowledge is stuck inside individuals. This type of thing would need to survive the relentless reorg cycle that seems ubiquitous in tech companies.

- The health sector seems to have longer overall tenures than the tech sector. At the very least this kind of system should somehow link into the HR administration, so that if a document owner leaves there can be an alert "This document is now unowned!". Of course, that alert also needs someone to monitor that.

- What would you use as a metric for the asset-ness of knowledge? Some types of knowledge seem more important than others, but it is not clear to me how to quantify that.

Your point about digital minimalism is very good though. A lot of things that should be deleted are instead kept around in a form of digital hoarding behavior.
r_hoods_ghost • on Feb 17, 2022
The way it works on a typical QMS (quality management system) of the type you use in healthcare is when someone leaves the line manager or quality manager has to go through and reassign any documents owned by the individual (and they're always owned by an individual) to someone else. It's very much part of the normal rhythm of business and you have to do it because if you're working in medical / life sciences you need to be accredited, and as part of the accreditation your QMS will be checked to ensure it is up to date and there's no-one one there that shouldn't be.
da39a3ee • on Feb 17, 2022
As a slight extension of this line of thinking:
Every document is either "live" or a "snapshot".

Live documents have an expiry.

Documents are snapshots by default.
phphphphp • on Feb 17, 2022
I don't have a great answer unfortunately. My best attempt would involve walking back my use of "knowledge" as both an asset and liability, and instead I'd try to add some distinction, i.e: maybe describe "knowledge" as the asset and "documentation" as the liability.
Knowledge is something you consume, digest and then use to inform thinking. New knowledge is built on old, and business outputs can be traced back through the knowledge that shaped them. Documentation, on the other hand, is a statement of fact(s) that are applicable only in a specific context (often temporal) that do not contribute to the evolution of a business.

Liabilities aren't inherently negative, they're a valuable tool in the right circumstance: a piece of documentation written for a customer support agent describing "how to issue a refund" has value but it can't be leveraged to grow the business, it can't be built upon, and it must be maintained. The business then must make a tradeoff between investing in knowledge or taking on liabilities.

If we were to represent this visually, knowledge would be the branches of a tree that other branches grow from, and documentation is a dead end.

Most of the documentation I've encountered in my professional life has been written to meet an arbitrary requirement for there to be "documentation" about an output, and so it's a rushed recital of the bare-minimum facts about a thing that exists. Nothing can grow from it. Whereas, when I've encountered it, the knowledge used along the way has been very valuable. A business can create an asset by capturing everything learned, and leverage that asset to inform the next decision, and so on and so forth. After all, that's what individual employees are doing already, it's just happening siloed in their heads.

Returning to the customer support example: years of knowledge collected about our business might teach us that our product's sizing is unique in the marketplace and many customers end up refunding their first purchase to order a different size. If issuing a refund takes 5 minutes per customer, and if all we have is documentation describing the 10 step process, a request from stakeholders to improve customer support efficiency might manifest itself as software development work to reduce issuing a refund to a 5 step process... but knowledge about the business would inform us that what customers really want is to ability to find the right size that fits. Rather than make a documented process easier, we might implement a purchase option where we charge for 1 item, send out 2 sizes, and the customer returns the one they don't want to keep. If all our business knowledge is captured, and not siloed, then a new employee should be able to theorise that, not only an employee who has been around from the start.

I'm not sure how confident I am in the way I've framed this, and using the word "documentation" seems like a risk because "documentation" means "everything written down" to most people, but I appreciate your question because it was interesting to think about: maybe someday I'll have more clarity in my thinking on this.
leftnode • on Feb 17, 2022
There's a piece of software (that I have no affiliation with) that has a feature like this built in named Guru: https://www.getguru.com
hifikuno • on Feb 17, 2022 • 3 more
Oh my god, the expiry date is an amazing idea. So much of our data is never updated, and forcing the creator to update it or delete it before the expiry date would clear up so much old and outdated information.
kaycebasques • on Feb 17, 2022 • 3 more
> After losing a few key personnel lately I have become painfully aware of the amount of knowledge stuck with individuals
Speaking as a technical writer who has worked deeply with engineering teams. You might be "missing the forest for the trees" here a bit by focusing on documentation technology rather than engineering culture. Your team doesn't feel compelled or rewarded to create documentation. Go to your head of engineering, CEO, etc., share the story of losing critical company knowledge when these people left, and suggest to them that the team needs to be properly incentivized to create docs. Make documentation a factor in promotion, bonuses, social recognition, etc.

The technology is more likely to take care of itself after that. Rather, you'll have more engagement from stakeholders and will have more confidence around what will work.

But beyond that, in terms of wrapping your head around information architecture, Divio's documentation system is a great start: https://documentation.divio.com/

You can hire or find technical writers to give brown bag lunches on documentation basics. I would do it for you. Poke around on my HN profile and you'll find how to contact me.

Last, I would set the expectation that it's OK to feel like you're winging the documentation. I suspect a lot of engineers don't write docs because they feel they are bad writers and don't know what they're doing. Just focus on creating a safe space to creating docs and keeping them up-to-date first. Over time as you all use each other's docs you will figure out why they suck.

The Write The Docs conference videos on YouTube are also an excellent resource.
maccard • on Feb 17, 2022 • 6 more
We use notion (https://www.notion.so/) but the tool itself doesn't really matter. Confluence, Notion, Basecamp, etc. We're a team of 20 people right now, and _everything_ lives in Notion. No "look at this google doc" or "go to <vendor>'s website", it lives in Notion. We can link to external vendors for "live" content, but PDFs are embedded, samples are zipped, etc.
Each page has an owner, a contact, and an expiry date. Owner is responsible for keeping it up to date, and if you see a page that is expired you can ping the owner (unfortunately we don't have "alert on expired page" yet). If the owner is unavailable, the backup should be able to answer any queries/update the page, and if they can't then the failure of that lies on the page owner. There are a few pages that have empty backups, by virtue of our company size, but all the critical stuff has an owner, backup and is checked once every month or two.
r_hoods_ghost • on Feb 17, 2022
Hoo boy, that's a tough one. One of my jobs is working for an ISO17043 accreditation provider so we have an ISO9001 QMS that all our docs sit on and every doc goes through an approval process, has a review date on it (6 months, 1 year, 3 years etc.), can have change requests, issues and non conformances logged against it, is included in audits and is written in a standard style.
We have a document controller who's job (not her entire job, but say 20% of her job) is just to ensure that documents are organised correctly, adhere to guidelines and are actually reviewed and updated when they are supposed to be (I.e. she will come and nag you if a document is overdue and you have been ignoring your notifications).

As part of the ordinary rhythm of business, metrics on how well we are doing on the document control front are produced and reviewed roughly every two months by a senior manager in a quality team meeting. If you don't keep up to date with your document control tasks it will be brought up in your appraisal (in a reasonable fashion, you might just have too many docs assigned to you).

There's other stuff, but let's just say document management is quite important to that business because procedures matter when getting them wrong kills people and / or leaves smoking holes in the ground.

Importantly the process of writing a doc is dead easy and anyone (literally, some of the most useful are written by the admin assistants and lab techs) can create one at any time. Theres a standard template and style guide, you write your doc, you choose an approval pathway, classify it and then submit it for approval. While it's waiting to be approved it sits in the drafts register with a warning on it saying not yet approved, but anyone can still access it.

In practice what happens is rather than writing a long email explaining how to do something you'll just write a doc, stick it in the QMS and give someone a link. Then when someone else needs to know that they can either find it themselves or you can just point them at it.

The admin overhead of the whole system is surprisingly small and means that we actually do have up to date documentation on most things.
otoburb • on Feb 17, 2022
>>There's other stuff, but let's just say document management is quite important to that business because procedures matter when getting them wrong kills people and / or leaves smoking holes in the ground.
If only other industries took matters as seriously, then an in-house writing culture would (should!) improve dramatically. Sounds like a necessary, yet still insufficient, requirement.
IG_Semmelweiss • on Feb 17, 2022 • 1 more
Former Notion customer. It failed for reasons that I should have predicted:
Your wiki is always destined to fail if you are never going to use it as part of your daily ops.

This is why our internal wiki with "Clickup" is working OK thus far. We use clickup because it allows us to create tasks from within our wiki and reference docs in our clickup wiki, and link the latter to tasks or even email chains. As long as someone organized is handling the doc repo and the wikis, its quite good.

In summary. Its great for meeting agendas and opening epics or tasks during the meeting so there's accountability (no GDocs). Its great for doc repo that is "alive" to replace Gdrive. Its great to start customer comms (email outbound that threads inside Clickup) within tasks that themselves are referencing docs in clickup. You could also have a true HR / company policy wiki if you wanted, but we are too small for that. Instead we effectively have an OPS wiki. I think Clickup has found a great product market fit within the B2B space. It may even be great for B2C too.

Full disclosure. We are a customer. We make no money from them in any way.

I also bet that Clickup will eat Notion unless Notion does something dramatic.
fasteddie31003 • on Feb 17, 2022 • 1 more
This is the exact problem I'm trying to solve with my startup https://GainKnowHow.com .
I think we have been structuring documentation ineffectively for a while. GainKnowHow structures knowledge by prerequisites in a Knowledge Web, which I think is the best way to figure out how something works.

My goal is to let you "program" your organization through skills in a Knowledge Web that represents how your organization runs. You can write tests to see if employees actually understand their skills and there are change management features that tell the relevant employees when a skill has changed through skill diffs.

Here's an example of how to train your software engineers https://gainknowhow.com/software-companies.html
buro9 • on Feb 17, 2022
We (Grafana) are just about to roll out https://www.simpplr.com/ internally.
We've been using a mix of tools until now, Guru, Google Docs... but have lacked discoverability, powerful search, and in Google the ability to create sites for teams, etc.

Personally I use Obsidian and the files are sync'd via Syncthing.

What I wish would exist: A markdown driven wiki with Git (or something like it) in the backend so that you can clone the info locally, or refer to the master version, and even stage big changes to an area, etc. - basically something halfway between Obsidian and Confluence I guess.
depingus • on Feb 17, 2022
I just spent some time looking at this. There's no reason you can't use Obsidian with git. Obsidian just saves md files in a basic folder structure. You can git init in the root of your Obsidian vault directory (.gitignore your .obsidian folder). There's even an "Obsidian Git" community plugin that does the git work for you.
To serve your md files as a traditional wiki in browsers, there's a git backed wiki named Gollum that also uses md files in a basic folder structure. https://github.com/gollum/gollum You can see where I'm going with this.

Gollum doesn't have user authentication or anything fancy, it just renders and edits md files. I tried it. There didn't seem to be a difference between Obsidian's and Gollum's markdown. When I committed my entire Obsidian vault to a git repo, I could still choose to have Gollum serve the entire vault, or just a subdirectory in the repo. I could also disable all editing in Gollum.

While Obsidian is working directly with the md files, Gollum doesn't update until I actually commit the changes. Obsidian is basically an IDE for my wiki now.

I was mostly satisfied with Joplin syncing to OneDrive prior to today's experiment. But now I think Obsidian + Git + Gollum deserves a closer look. It might be a bit overkill for my personal wiki, but it could work in a team setting if everyone works on the wiki like they would a normal git project.
polote • on Feb 17, 2022
Simpplr is in my opinion an inferior tool to Confluence or Notion. It works mostly well for static information and as a enterprise search tool, but won't help improving the underlying culture.
As for you ask, the best solution that I've found, is to let people document things on Github and index those documents in another tool. That way there is no duplication, you let people use the tool they know, can use Markdown, but still benefit from searching, assigning owner, up to date date, rights ... That's how we do it at Dokkument
jka • on Feb 17, 2022
Have you heard of / explored Athens Research[1] (brief summarization: open source, multiplayer-if-cloud-or-self-hosted, YC-backed)?
[1] - https://www.athensresearch.org/
yabones • on Feb 17, 2022
My solution (for personal notes etc) is to make a git repo with markdown files, then render it all with mkdocs on every push. In the past it was just a cron job running on a dumb little webserver (git pull && mkdocs build) to push the new changes every x minutes. Nowadays it's a bit more sophisticated with netlify building on main & PRs. Both are completely valid!
Obviously it's not user-friendly at all. Only people who know how to use git can use it, which isn't great for collaboration with non-techie folks. Ideally, I'd build a little editor widget that could be embedded in the page...
dotancohen • on Feb 17, 2022
  > A markdown driven wiki with Git
This is exactly what I do. Though lately I've been transitioning to org-mode for non-personal notes as I don't need them on mobile.
Your users can use any Markdown editor that they like. But one person should be responsible for creating new documents, so that there will be consistency in naming and placing in the hierarchy. Naming things is hard, leave that part up to the Knowledge Base owner.
denton-scratch • on Feb 17, 2022
> leave that part up to the Knowledge Base owner.
Well, that's against the philosophy of a wiki. Also, in a small team, nobody is the "knowledgebase owner" - he's just another developer. Putting a human in the workflow creates friction. But I'm totally with you on the "naming things" problem.

A full-blown corporate knowledge management system is a repository you can throw anything into - invoices, emails, memos, reports, etc.; the system will automatically generate a knowledge taxonomy and article summaries. But such systems require much more maintenance effort than something simple like a wiki, and are overkill for a small team of developers.
mplanchard • on Feb 17, 2022
On iOS, PlainOrg and BeOrg do a good job of making your org notes readable, searchable, and (basically) editable. I have heard there are good apps for Android as well, but I can’t vouch for them personally.
xenodium • on Feb 17, 2022
Hey, nice surprise to see Plain Org mentioned (author here). Glad you find it useful.
mplanchard • on Feb 23, 2022
I’ve been using it since beta! It’s a great app, and I’m grateful to you for making it!
kaycebasques • on Feb 17, 2022
One lesson learned from leading https://web.dev is that a lot of people, even technical ones, aren't comfortable with git + Markdown. And then there are people who are comfortable with it but feel that it's too much friction for simple docs updates.
dotancohen • on Feb 17, 2022
For those who are uncomfortable with Git: My personal git notes repo has this script right there in the document root:
  $ cat ~/Notes/sync.sh 
  #!/usr/bin/env bash
  git add *
  git commit -am "$(hostname)"
  git pull
  git push
  echo ''
  git status
That's good for 99% of my own use - and I'm a technical user. You can leave those last two lines off and redirect stdout to /dev/null. If there's an error on "sync" the user can call you over to handle what will likely be either a merge conflict or a network issue. Even for Windows users you can probably wrap that in a .bat file to be double-clicked on the desktop.
And there are a ton of WYSIWYG Markdown editors. I've used Typora in the past.
tempest_ • on Feb 17, 2022
WikiJS can store its files in git (https://docs.requarks.io/storage/git) though it is not exactly easy to run as a stand alone app.
therealasdf • on Feb 17, 2022
AzureDevops wiki is exactly that. A git repo for markdown files
pxtail • on Feb 17, 2022
For some documentation we are using https://www.bookstackapp.com/ , we have also few instances for clients internal docs.
What is especially nice (less for us, more for some of clients) is that it has clear, understandable and working out of the box ACL system in place - and this is not obvious or easy to setup/configure for many wiki-like projects out there.

For maintenance and filling knowledge-base - I think that what's works for us is establishing and following rules, for example: one cannot mark feature as complete without creating/updating documentation page related to it, documentation maintenance is checklist element of task completion flow.
pabs3 • on Feb 17, 2022
The Diátaxis documentation framework is one I heard about recently, Ubuntu/Canonical are switching to it:
https://diataxis.fr/ https://ubuntu.com//blog/the-future-of-documentation-at-cano...
hdjjhhvvhga • on Feb 17, 2022 • 4 more
Old style - an "intranet" wiki that is linked to from the main internal company page. No orphaned articles - each needs to fit in the hierarchy somehow that is obviously quite flexible. Searching is easy and gives instant results. As opposed to the current version of Google, you can use search operators and they work as expected. Because managers embraced it and encourage their reports to (actively) use it, it works - most of the time.
The biggest challenge is outdated information: since the responsibility is shared, sometimes I come across articles that haven't been updated since 2011 - for example, because somebody left, and I see some bits aren't up to date anymore. But I feel uneasy about deleting the article or just doing anything about it unless it's one of "my own" or directly related to my department. But in spite of that, I think it's working quite well overall. I used Confluence in another company and it felt too invasive and in the end nobody used it.
amattn • on Feb 17, 2022 • 1 more
I'm working on a solution to this called KB Clip: https://kbclip.com
basically it's a slack add-on that allows you to turn a conversation into a web/wiki page in just a few seconds. Essentially, lots of important, KB-worthy info happens naturally during the course of work slack conversations.

The idea being that making knowledge capture easy kind of naturally makes the usage of the knowledge base happen. KB usage is kind of a chicken and egg problem. if no one creates info, no one will look there.

We don't currently export to Confluence, but the plan is to export to most of the major wiki/KB platforms. We're going thru Slack App Directory approval process at the moment, but we're planning on doing a big marketing push as soon as that happens.

happy to answer any question about this topic or the product we're building!
fsloth • on Feb 17, 2022
"It's hard for me to just work on the docs as I feel like I should be following some sort of standard as I do it."
Some standards come to mind: Microsoft's Style Guide (https://docs.microsoft.com/en-us/style-guide/welcome/) and Strunk&White's "Elements of style"

But if you feel writing should have standards, then you might to need to write those standards yourself. Which is not a bad idea at all - you just need to approach it as a journey of discovery - which standards are helpfull, and which are not. It's not something that can be got exactly right from the beginning.

Github's issue reporting functionality fills in automatically content hints.

Maybe you could start from headline template with content hints, and evolve that as need arises?
turkeywelder • on Feb 17, 2022 • 1 more
All the business knowledge is in Basecamp as that's where all the "work planning" is done. If you want to find out how a specific feature works, or how the decisions were made for that, go find the project in Basecamp, it'll be archived if it's shipped but it's still searchable.
For new dev setup/infrastructure stuff we use a github Wiki and the new starters point out issues in that for us - their first tasks are to update it if they find issues or missing info because it forces them to go and dig around to find the knowledge islands - they're the best people for it because it's who we want to solve the problem for.

Admittedly we've got a small company and a nice tight tech stack but there's still tribal knowledge in 2-3 people's heads and distilling that out to the team is a slow process of pair programming and explanation.
furstenheim • on Feb 17, 2022
I've always found that wikis are too far from the code.
To have any chance of being up to date, knowledge of the code and functionality should be as close from the code as possible.
hifikuno • on Feb 17, 2022
I have thought about doing some sort of auto generated documentation based on comments, I know some other languages do this. I shall look into this further.
freedomben • on Feb 17, 2022
exdoc in elixir does this, and it is wonderful
luka-birsa • on Feb 17, 2022
We're happy users of Confluence (SaaS version) and try to store all knowledge there. At 50 employees we have multiple teams approaching the Confluence as a KB with various success so there are a couple of takeaways.
1. You need to mandate that everybody uses one tools and push for the use from the top down as well as showcase the use bottom-up.

2. Split responsibilities on a per team level; eg people working on product lead the product confluence page, people working on hardware lead the hardware confluence page...

3. Try hard to push all relevant discussions and decisions to the same KB.

4. Request that leads schedule time for updating knowledge base (we sometimes push for this via OKRs).

5. When people are leaving the company, we primarily push that they update the KB to the maximum (other work is not important after they give notice).
thrower123 • on Feb 17, 2022
A succession of wiki products that are essentially write-only. No one ever reads them. Eventually somebody gets frustrated with the disorganization and says "We should switch to Yet Another Wiki Product" and the cycle begins anew.
adrianomartins • on Feb 17, 2022
I feel we've been in the same spot as you. We had a wiki (google sites and google drive with a lot of documents) but information would become inaccessible from time to time, to the point it was pretty much useless. We eventually understood that the knowledge sharing/maintenance was simply being an extra step in our work, a mostly disregarded one, almost an after thought.
What we did was to put knowledge at the center stage, make it as easy as possible, pleasant to maintain, and avoid at all costs new/extra tools. We eventually settled for Notion. I'm sure you can find about notion benefits on your own, but essentially it does all that. It's super intuitive, easy and beautiful, easy to get around (albeit sometimes slow). Get everthing in the same place as much as possible, with every new tool you'll loose out (knowledge bits here and there, extra connections that stop working, or that people don't bother to check)

But getting a good information platform was only half of the story. We needed to start thinking and working differently. We decided that if we ever make a decision, or arrive at a conclusion, that's worth sharing, then it should be worth writing. And it's by doing this, and expecting all other team members to do it as well, that we arrive at this stage.

I'm sure this doesn't work for all teams, and other teams probably arrived at other, even better solutions, but this was what worked (wonders) for us.
hifikuno • on Feb 17, 2022
I have used Notion before personally and it's a sweet bit of software. We're already an Atlassian shop, using Bitbucket, Jira and Confluence. Up until very recently we were barely using any of it but my team just moved from SVN to Git (about bloody time) so when we started using Bitbucket it started to ball rolling with the rest of the stuff.
I like the idea of any sharable decision or conclusion needing to be documented. We are a data warehouse for our organization and so we rely on business rules ALOT. So many of those business rules live only in the code with no explanation and no one remaining who can explain it.

I think we're at the turning point of beginning to think and work differently. I'm going to start with my small team of three, and once we get going then try expand it to the rest of the department. It is kinda hard as I don't really have the authority to enforce it, the best I can do is strongly suggest.
blindluke • on Feb 17, 2022
> My problem is, I know that we are missing information, what I don't know is how to tease out that information from myself and other coworkers.
I would start by reflecting on the way in which getting that knowledge out of the coworkers into the knowledge base is incentivized.

I keep my notes in markdown files. A lot of my coworkers use Obsidian, CherryNotes, OneNote, and I'm sure that there's a dozen other solutions out there. Keeping notes locally is actively encouraged by the fact you can't rely on the Confluence server to be up after business hours and the fact that the centralized knowledge base upgrades destroyed our documentation efforts twice over the past 10 years.

I also keep my notes short, omitting everything that's obvious to me. This makes them less valuable when it comes to knowledge sharing, but makes them better for me - short notes mean less visual noise to filter out. Writing a version of those notes that's more comprehensive is extra effort. That extra effort needs to be visible, treated as 'real work', encouraged and valued. Otherwise, I will prioritize other tasks that are visible, treated as 'real work', encouraged and valued.

The first thing I would worry about is making sure the central knowledge repository is as convenient as the local notes. Then, I would examine if creating / updating documentation in the central repository is encouraged, and in what way.
nickjj • on Feb 17, 2022
I use Obsidian for my own notes that only live on my machine, then they bake there for a while until they get refined enough to turn it into something that others can read in which case it gets published within Confluence.
Personally I'd rather see a knowledge base that is in pure Markdown, perhaps a static site that auto-publishes on push to a specific repo. I just like the idea of being in control of the text, plus it means you can write these docs in the comfort of your editor instead of using a slow web UI. Right now I end up writing it offline and copy / pasting it along with formatting it in Confluence afterwards, it feels like a little wasted effort.

We try to reserve these types of docs to be guides, it's more like blog posts not so much a detailed instruction list on how to use some library or app. This way they don't really get outdated because a library or step changed.

I'm a big fan of never deleting guides and notes though, for the not needed ones I'd still keep them around but maybe move them into an archive section. Really, a static site generator has all of the tools to make a really nice system for this. You could also spend a day to make a little back-end to offer full text search too.
pphysch • on Feb 17, 2022
There's lots of discussion about this or that wiki, Notion, etc. but IME this contradicts how knowledge primarily flows in 2022.
Most of the time, when I need to know something, I have a specific question. So I throw some keywords at Google and Google responds (rarely) with the answer, or (more commonly) with a relevant stackoverflow link.

What if you had an internal "stackoverflow", i.e. Q&A platform?

Obviously, wikis and documents still have value. They're important for onboarding new employees and roles and getting everyone to a baseline understanding.

However, 99% of the time, the employee wants to know the answer to an explicit question like "How do I remove a user from X" or "how do I reset/update the Y service". Digging through documentation to construct an answer is a lot of work, and should be cached somewhere other than the employee's brain.

With a SO-style format, you get a) a quick answer and b) context about who answered (without digging through separate history interfaces) and c) an informal log of how processes have changed over time. It's also very easy and informal to add a new question or answer, without worrying about formatting conventions.

Are there tools out there to support this?
michaelsalim • on Feb 17, 2022
Stack overflow teams exist. https://stackoverflow.com/teams/pricing.
At $COMPANY, we tried this and it was a waste of time. The problem is you need someone to answer the questions. So instead of looking at the wiki or asking the relevant engineers in person or slack, you now have to write a question & wait for somebody to answer. Somebody eventually answers but it was wrong and now you're back to slack asking the relevant engineer anyway.

I can see why it could be useful like how StackOverflow has been. But the early days will be painful and unless you're working in a huge company, I don't see this being worth it at all.
anthuswilliams • on Feb 17, 2022
SO itself offers a private version of its project for this purpose.
brongondwana • on Feb 17, 2022
The important mental change, and it's a real challenge - is to realise that your knowledge of how the system works in your head is cache rather than live data, and that you need to check the document for how to do it. So if you change something, you write it to permanent store, not just to the cache. Which means it's not the new way to do something until it's the way that's written into the knowledge base.
polote • on Feb 17, 2022
It is all about details. What you want to achieve is what we call a written culture.
The only general advice that we can give you , will be pretty vague. Like get everyone to agree that it is important, start documenting yourself to lead by example, reference the documentation as much as possible when it exists, curate information so that out of date is marked at out of date, encourage your colleagues to document specific things, make the process about them and not about you. Changing culture is hard, and even harder when you don't have past experience doing it or not much support from your executives.

I'm the founder of a product solving those issues, but I'll be the first to tell you that the tool doesn't matter a lot. Some are better than others, but none can balance a culture in which documentation has not a strong place.

If you (or anyone reading that) want help to improve things in your company, I'll be happy to jump on a quick call with you (no trying to sell you anything, just advice in your specific case) reach out to me at paul at dokkument.com
tlarkworthy • on Feb 17, 2022
I advocate rotating roles, and having an operational doc, the trick being people have to repeatedly read and update the operational doc to fill the role they have just been assigned.
Mandating the doc stays up to date when noone is actively using it is an exercise in time wasting

The problem you are facing is the weakness of having individual specialists. The problem is not the doc maintenance but organisational
WJW • on Feb 17, 2022
How do you manage rare events in such a setup? For example, how to restore a database from backup is valuable knowledge that should be documented somewhere so you don't have to make it up as you go along. At the same time, in (almost) every place I've ever worked at this was not required very often.
This seems like something chaos engineering and/or a proper ops team with regular disaster exercises would be able to pick up, but (like you mention) in most startups those seem to have very low organisational priority.
thenerdhead • on Feb 17, 2022
Depends on your position.
If you have role power, then set aside time to work on documentation.

If you have to lead with influence, you simply just start doing and others will follow. One of the best things you can do is document and show people how you manage the knowledge base.

Secondly, you have to delegate. Nobody knows everything, you have to ask for help and regular contributions. Just be up front and let people know your intention and they'd be more than willing to help.

Lastly, take regular notes. For areas that you have little to no idea about but others talk about all the time in PRs, meetings, and more, you can extract that knowledge to the point of having your best shot at making the docs as correct as possible and then you can ask for a review from someone else.
remorses • on Feb 17, 2022
If you are searching for a way to make docs more accessible to everyone and publish them as a knowldge base website for your users check out notaku.website/product/docs
It takes Notion content and generates a docs website

I am the creator of this tool so don’t hesitate to give me any feedback
olegp • on Feb 17, 2022
We use Nuclino: https://www.nuclino.com/
Jefro118 • on Feb 17, 2022
Same as another commenter, I try to make it a habit of either referencing documentation when I need to answer a question or making a note to fill it in when I can't find a reference.
For searching documentation there's a lot to be desired too so I'll make a shameless plug for my side project: https://neat.wiki. It's a simple wiki creator on top of Google Drive but I'm layering on some GPT-3 goodness for semantic search and question answering so you can always find what you're looking for.
gwbas1c • on Feb 17, 2022 • 2 more
> Currently I am stuck with Confluence...
Try Google Drive

FWIW: A previous job used confluence, but my current job just uses some shared folders in Google Drive. We set up a shortcut to search these documents in our browser.

The search functionality is significantly better than Confluence. You just gotta accept that Google Drive doesn't look as "organized" as Confluence.

Another thing we do is search through Asana.

The big thing, though, is you need to encourage a culture of note-taking. Take notes in tickets. Write documents in Google Drive (or whatever wiki you use.) Make sure that your ticketing and wiki system have good search.
denton-scratch • on Feb 17, 2022
Last place I worked (about 15 people), we needed a knowledge store. So I set up Mediawiki, mainly because I know Mediawiki, and I like wikis. It started filling up with articles: about the dev tooling, the servers, the services and how to use them, deployment processes and so on. New people were onboarding every few months, and it was definitely useful to have the knowledge recorded somewhere.
What I didn't do is to design a knowledge schema. At what level of granularity should an article be? What umbrella topics should act as portals to articles? This is hard, and with Mediawiki it would be impossible to enforce anyway. So the knowledgebase grew like Topsy ("I just growed"), and had no structure.

I set up the system because I was (part-time) the sysadmin, and my skull was rapidly becoming a repository for a lot of technical information about how the systems worked. My memory is not so good, and I needed to pickle that information before I retired. So a lot of the initial articles were created by me, as fairly detailed "note-to-self" articles, and how-tos for my colleagues.

In retrospect, I suspect a tool other than Mediawiki might have served us better; but I was in a hurry to scratch my itch, and I had other duties. I think a more opinionated note-taking tool might have enforced some kind of knowledge schema. Mediawiki isn't good for representing knowledge as a hierarchy, in particular.

I don't know much about note-taking tools, so I still have no idea what alternatives there were. In the event my colleagues did use the wiki, both to recover knowledge and to store it. From that point of view it worked; knowledge was being saved and retrieved. But even a collection of text/plain files would have been better than nothing; the wiki wasn't used because it was good, I think, but because we needed something.

So I'm suggesting that if you have nothing in place, then almost anything is better than nothing. Whatever that something is, it should be able to export stuff in an easily-parsed format, so that you can import it to a better system should you decide to migrate (a collection of text/plain files would seem to fit that bill).

I'm not offering advice, other than to try something more opinionated than a wiki. I'm really offering anecdata.
kaycebasques • on Feb 17, 2022
> What I didn't do is to design a knowledge schema. At what level of granularity should an article be?
We technical writers call this information architecture. It's a tough problem even for the people who do this every day.
EnKopVand • on Feb 17, 2022
After a decades worth of working in non-tech enterprise and small companies. Which means I’ve worked on major projects, minor projects, as an advisor and later implementation guide to external developers and so on, I’m not sure I’ve seen a good recipe that doesn’t involve making sure that people work together on the same things ever so often and to keep things as simple as possible.
I’m not saying that you shouldn’t build generic things for code-reuse and easier maintaining. Because you should, just be aware that as soon as you build a generic something, you’re likely stepping into the land of someone’s headspace, and other people might take a while to understand that. Which is where working on each others projects, or doing code reviews help in my experience.

I still encourage good and clean documentation. Something that quickly tells the reader what X does and why it does it.

I also encourage everyone to draw what connects to where and how it does so. Not in any form of detail, just so that you don’t end up in a situation where you have to doable a SQL user to find out who screams about it.

I’m also personally a fan of writing to-do-lists containing all the steps I took to make something work. I recently wrote one for how to connect sequelize to an instance msSQL server in azure. It wasn’t trivial, and because it involved a lot of trial and error, it’s something I couldn’t repeat again in two weeks if I hadn’t written down the steps that worked.

Good question though. It’s something we should all work on.
lamontcg • on Feb 17, 2022
IMO you need to keep it small and active and if you have old documentation you need to have the courage to delete it, or at least move it to some archived knowledge base that doesn't pollute the search space of whatever you're using.
The way knowledge bases die is they get cluttered up with irrelevant information from years ago which someone wants to cling to because somewhere in the mountains of useless information there might be that one gem which they cannot fathom throwing away, even though they don't know what it is.

There's a really common perceptual distortion here where people dramatically overvalue that one piece of information they might throw away vs. the corrosive effect of all the information which is crap (and the enormous effort required to sift through every single piece of information and one-by-one search for that gem and rescue it rather than just bulk tossing away things that are in areas which never get touched).

Which is not talking about the system which is ten years old which was documented five years ago, which every year is super critical to understand how to maintain it or whatever. But you know where that documentation is at because it saves your ass relatively repetitively. It is everything else that was written 5+ years ago that you've never once looked at which is the problem.
mrwnmonm • on Feb 17, 2022
I was thinking about using https://obsidian.md with a shared file on Google Drive, but still didn't try it.
theshrike79 • on Feb 17, 2022
Obsidian is awesome for personal use, but a company-wide Obsidian on a Google Drive just smells like a disaster waiting to happen.
No version control, no edit history. Sheesh.
hifikuno • on Feb 17, 2022
I personally use Obsidian and I love it. It has a great community (free) plugin you can use which will back your documents up to GitHub if you want.
Unfortunately, I am bound in the software I can use for the task as we already have Confluence and I am not in a position to change that.
7thaccount • on Feb 18, 2022
I've written hundreds of pages on our wiki. One other coworker has written a few dozen. Everyone else has written like 0-3 entries. 99.99% of people really hate documenting stuff. I'm not sure why unless someone has a photographic memory. It is amazing to have someone ask you something about an obscure process or subject and remember that you explored it and documented it in detail 3 years ago and can get back up to speed in 10 minutes rather than 10 hours.
bingo-185 • on Feb 17, 2022
The diataxis framework may also be useful for organisation here https://diataxis.fr/
lifeisstillgood • on Feb 17, 2022
I was writing something called soppy (Standard Operating Procedures py) which something like that has been up recently. the basic idea is to have (online) checklists that at first are nothing more than 1. do this 2. fill in that
but each process can have a stage replaced with actual code - so eventually you have a part manual part automated process that is fully self documented

A few other people have same idea - I am sure there are some commercial versions
svilen_dobrev • on Feb 17, 2022
IMO unless there is some technical writer around there, which job is to put that doco right - extract the info from people heads, combine it and word it properly.. it's not happening. For 30+ years only few times i have not been the lonely editor of the project wiki (or whatever knowledge-base).. and i dont like doing it either.. but have to, as it's worse otherwise.
Writing (succint, correct, tautological where needed and non-dubious all-over) text is very hard, and very very different to coding, or any math-like thinking. Because the human language allows to do anything with it. (Esp. if foreign language, that adds another dimension to what that anything means). It needs (skill and) different frame of mind, and switching to and from isn't easy.

Which is probably main unspoken reason why developers avoid it (most techincal people actualy, mechanical engineers also dont really like writing documentation) - apart of other usual reasons, like lack of time, whatever..
Dachande663 • on Feb 17, 2022
Started releasing https://www.waybook.com recently. It's initially aimed at onboarding, but turns out lots of folks like it for the structure it defines. Used Confluence before and things just got lost in a folder in a folder in a folder.
escot • on Feb 17, 2022
Docs become stale and untrusted. Theres a tech solution waiting to be made that orients docs around time instead of hierarchy or tags. Kind of like how a commit tells you something was true at a certain time and in a certain context.
But I also agree with other commenters that culture is a huge part of this.
oldandboring • on Feb 18, 2022
Yours is probably the comment that most resonates with me. The whole thing with team documentation is that you're asking the employees to do something most of them don't want to do, which is make every development or devops task take longer. You have to retrain them to think "okay I just changed something. do I also have to update documentation?" and then, if the answer is "yes", they have to actually go and update the documentation. It's clearly not impossible but it's a big change for many devs and, in my experience, the result is exactly what you describe: stale docs which are therefore untrusted. Maybe one motivated leader will try to be the hero and maintain the docs, but that just makes everyone else even lazier (I don't think about the docs, Joe handles that) and eventually he/she will give up or leave.
ivoras • on Feb 17, 2022
We went with Notion and while it's a Jack of all trades (it can be a wiki, a database, a public-facing web, an issue tracker, or a combination of everything at the same time), and needs a bit getting used to, we haven't regretted it and find the wide array of features very useful.
iamwpj • on Feb 17, 2022
It's almost never a software issue. If you had another application besides Confluence would you be suddenly motivated to document? I doubt it. It's discipline and habits. The boring stuff. Tickets and projects should always include a component of documentation. Document about things, avoid how-to's except for specifics. Don't worry about screenshots, GUIs change all the time. Summarize uniqueness and put annotations on why something is set a certain way.
I'd write a book about documentation, but I just haven't had a chance to get it all down yet.
bingo-185 • on Feb 17, 2022
https://www.serviceinnovation.org/kcs/
You should look into the Knowledge Centered Service methodology
PPACI • on Feb 17, 2022
We’re using the good old SharePoint with a lot of word / PowerPoint in it. Actually PowerPoint is really nice to describe different aspect of the same object. One slide per topic.
Everyone can search for it online, or un MS Teams. It’s versioned and everything.

We can easily export to markdown or even reveal.js (for ppt) using pandoc.

Once you get over your personal dislike of Word, honestly it works quite well!

The tech might not like it at first, but it’s waaaay easier to onboard non tech people into writing docs.
okaydeveloper • on Feb 17, 2022
For my team, it is Github + Slack + Google Drive. Most of the ongoing discussion/planning is on slack which we try to maximize by adding each activity we can there including screenshots of imp conversations, ideas and decisions made. We store all the work including creative output and more structured plans/data on company-wide shared Google Drive. Github stores all the code base and product documentation.
autarchprinceps • on Feb 17, 2022
I'm sorry, but documentation is a waste of time. It is never complete, never up to date, never easy to find something in, etc.
Spend the time to make whatever you are doing self describing. Write cleaner code, use infrastructure as code, ci/cd, automatic service overview, proper sprint planing, etc. Anything that improves everyones day to day life, even if they have all the information, experience, etc.
62951413 • on Feb 18, 2022
Have you maintained code bases not written by you much? Have you worked in teams of 10+ people long enough to see people leave the company?
You can never write down too much. Please * write meaningful JIRA descriptions and try to have PRs linked to the ticket * always have a README.md that explains how to build/run/deploy the service * create and maintain a runbook document (another md file?) with frequently used commands and hints at debugging previously observed problems * add comments on class responsibilities and business rules * have a few unit test-like "tests" that make the service execute its main flow
mmusc • on Feb 17, 2022
The startup I'm working on right now is actively trying to solve this problem.
https://workpilot.io The platform is part wiki/ part proċess management tool. After lot's of user discussions it became apparent that lots of business know how falls into those two categories. With the latter being easier to reuse and track.
dataspun • on Feb 17, 2022
In a large org with “enterprise” tools deployed I find that a combination of Box and Jira is a tidy solution. Engineers, analysts, managers, partners, vendors, and other stakeholders can all contribute and be provisioned secure access to the docs as needed. Definitely requires a high degree of organization, incentive, and accountability to make it hum but the effort is worthwhile.
jcpst • on Feb 17, 2022
Trying to make this better. Finding something sometimes involves a combination of tools that have been adopted over the years.
Hoping to get SO for teams.
kaycebasques • on Feb 17, 2022
Stack Overflow for Teams makes a lot of sense to me as a key component in managing company knowledge. There is great power in formulating everything as questions and answers. And the voting system helps you organically track which knowledge is still up-to-date.
eigilsagafos • on Feb 17, 2022
We are building a tool that can help you tackle some of this pain through process visualization. Built to be easy to use and create alignment across teams on how different aspects of your business works. Check us out! https://shiftx.com
nicholasbraker • on Feb 17, 2022
My BSc thesis was about knowledge management and this subject has always got my attention when it comes up. I work for an infrastructure consultancy company which employs 300+ engineers/consultants/architects over a wide range of customers. The main issue is what I call the "content versus context" problem. For example: A new engineer comes in and has a basic skill of a certain technology. Let's say he/she is well educated in Cisco routing and switching technologies. So the "content" of a certain technology space should be no problem. The challenge is the context: How does "skillset x/y/z apply to customer x/y/z" in which the specific customer operates in a certain context with its own constraints etc. In the aforementioned example: How does customer x/y/z uses Cisco technologies in what kind of architecture serving which specific services? The context is key and exploiting (in the positive sense) this knowledge is what you typically strive for to get employees up to speed with a new customer. The issue is (what you describe) how to make this contextual knowledge tangible and searchable in the least frictionless way. Within my shop there were different trains of thought:
1. Using fileshares grouped by customer (but this needed updating and not all employees uses those shares to file their work. Let alone the fact that sometimes it is not permitted to store confidential stuff on our own fileshares. We also do defense contracting work so that is a big no-no) 2. wiki's (already mentioned here), but this needed constant updating and for some the actual "coding" and using the markup language of a wiki was too much of a boundary 3. Using Yammer/Slack etc. This works OK as it is pretty low level, but it needs a certain critical mass to use and when you have 300+ employees with all kinds of customers who might also use their own Slack/Yammer what-have-you it's hard to get the employees conditioned to also check the internal channels each day/week.

We finale settled at the following mechanism which is a nice starting point to solve the "content/context" problem namely using the resumes each employee has to keep updated (and fiercely enforced by HR) and using a smart search algorithm to find the best knowledge-match of each employee. It doesn't work flawlessly and it had to be customized for us, but it works better than other methods. It's still a two step approach:

1. Search the CV for the best content-context match 2. Call/mail/IM the colleague and try to figure out if his/her knowledge helps you in tackling the issue you have.

Another method I saw someone use (and apply within a large online retailer) is to "tag" each person with his own knowledge set and visualize the links between them. So, again using my field of work as an example: Bob has a lot of knowledge (explicit in the form of certs etc.) of Palo Alto firewalls and is considered the internal "guru" in this specific field. The more Bob gets consulted for his knowledge the larger his "circle" of knowledge is (you can actually visualize this). What you eventually build is a knowledge graph were each point in the graph represents an employee with a certain knowledge set and every time he/she gets consulted for that specific knowledge by another employee a line is formed. This is a very powerful system but requires maintenance to update the knowledge sets. Setting this up requires interviewing each employee with questions like:

- What is your skillset and how do you score on a scale of 1-5 (or whatever scale one sees fit) in this specific set? - Who consults you the most for this knowledge set? - Who do you consult the most for which knowledge?

The end result is the aforementioned "chart" with "dots" representing ones knowledge. The larger the dot/circle the more knowledge one has.
katet • on Feb 17, 2022
I don't see a comment here for MkDocs, so I'll mention it.
It was started as a pet project for development knowledge, specifically migrating to local Docker-powered development environments. Initially that was all it had: the "how to set up the Dockers" page and a couple of other tidbits.

Over a period of time - years, frankly - it has grown into something a bit more useful, although still woefully short of where I would like it to be.

A few things have happened though:

* The first principle was: if I find something I have to "re-discover", document it

* The more it grows, the more useful it becomes. It's quite pleasing to be able to respond to a Slack message with "read this and tell me if you still have any questions"

* It's still slow going, but after some departures ourselves, we've seen a bit more interest in adding and codifying the "tribal knowledge"

The best things I like about it?

* It's statically hostable: GitLab/GitHub Pages, or if you need to wrangle it, `scp`/`ftp` it from a CI pipeline with a private Apache/NGINX deployment

* It's Markdown text embedded in the repository: you can grep it, or search it from VSCode/Sublime/any-IDE-of-choice

* It's Markdown text embedded in the repository: there's no way I can think of to make it easier for devs to contribute and maintain it than making it part of the same commit, the same MR, the same CI pipeline

* It's Python. Every Linux/OS X machine has python, so there's a minimal barrier to entry for previewing locally

* A bucket-load of plugins: Mermaid, PlantUML, SVG embeds, and more: https://github.com/mkdocs/mkdocs/wiki/MkDocs-Plugins

* The "Material for MkDocs" theme: https://squidfunk.github.io/mkdocs-material/

Nothing stops it becoming just as much of a mess as Confluence, but there's something slightly ineffable about being able to work with your docs as if they were code: refactor them! Reorganise, dedupe, and take MRs to fix stale articles/mistakes.

Other commenters have mentioned incentivising the docs, but I would finally add that someone, somewhere should take a principled stand around the organisation of the docs (and of course, give them space to fail, and experiment, and try again). Broken links are better than no links in the first place, since search is pretty accessible.

I was originally inspired by the documentation structure outlined at https://documentation.divio.com/ - although our organisation has evolved away from this into higher-level topics with subsections similar - but not identical - to the original idea.

Edit: as for the comment about Confluence, this is one of my favourite bits. You don't need "buy-in" for this, there's no subscription plan you need to approve.

If there's a concern around "split-brain" docs, I've used a guiding principle to defuse those conversations:

"Do these docs make sense if you don't have a local checkout of the repository?"

If the docs aren't related to the code repository - RCAs, business requirements, org charts, HR procedures - leave them in Confluence.

If they are related to the repository - coding standards, test coverage generators, docker/unit test commands, migration seed data - then what's the value-add for them being in Confluence? Your CEO isn't going to read them. Marketing don't need them. Put them in the codebase, and reduce the signal-to-noise in Confluence for the rest of the business.
kaycebasques • on Feb 17, 2022
> The more it grows, the more useful it becomes. It's quite pleasing to be able to respond to a Slack message with "read this and tell me if you still have any questions"
People have mentioned this in other comments but it's worth repeating that this habit is the true key. Make docs part of your core workflow. The other great things is that you're making them aware of the docs site (when they see the link I bet some have said "wow I didn't know we had this!") and you're specifically asking for feedback on where the doc is lacking.
dotancohen • on Feb 17, 2022
Automation.
No, really. Automate what you can. The best documentation is running code - it's the only documentation that is correct.
cloudengineer94 • on Feb 17, 2022
If more than one person asks me the same thing, then it's because I need to document it :-)
koliber • on Feb 17, 2022
Here are things that I do to improve the documentation situation. They are not perfect, and the results are not immediate. Over time though, I notice how they contribute to a more useful set of documentation.
- hyperlink, hyperlink, hyperlink. Anything relevant should be linked from at least one, and preferably multiple relevant places. That Tim Berners-Lee guy was on to something. More on this later.

- many tools use a hierarchy (e.g. folders) as the primary way of organizing information. People have spent countless hours arguing about the correct organization of this hierarchy, or the best location for a document. Don't do that -- it's a waste of time and you'll never get it right. While hierarchies are often useful, it is not as important where in a hierarchy a document lives. Hyperlinks allow you to link documents that relate in various ways, creating a graph of knowledge. The hierarchy is just one of the ways those links can fall.

- don't fret the tool. Information can live in Confluence, Notion, a wiki, Google sheets, presentations, GitHub READMEs, public Slack channels, recorded Loom videos, and the list goes on. Hyperlink relevant things together. If you have a postmortem document, link to slack conversation. If you have a document describing a performance improvement, add links to relevant git changes, or recorded demos. Use the best tool for the job, and hyperlink things. Prefer tools that allow hyperlink addressing.

- hub documents rule. Each team has a hub. Each project has a hub. Each process has a hub. Each department has a hub. A hub is an index, a homepage, and a starting point. If someone is looking for something, they can follow the hubs. If you want to find out what the metrics on project XYZ are, remember that team Houston did the project, go to their hub, go to their project list, find XYZ, and hopefully you'll get your answer.

- encourage a culture of common ownership of all documentation from the start. All documentation goes out of date and no single person can keep it up to date. In the onboarding, I tell each team member to modify the onboarding documentation any time they hit a snag, have an unanswered question, or see something that is unclear or wrong. Doing this on day one gives explicit permission to edit documentation. With modern tools, there is an edit history so there should be no fear of losing things. It seems that people consider creating and updating documentation someone else's job. And not in a bad way, but rather in a "I'm not allowed to do it" way.

- someone else said this, but if you are answering a question on Slack, email, or a PR review, spend a bit more time writing a clear response, and then add it to your wiki. Then, write a quick summary and include a link to the newly-written document. Do this a lot, but use a positive tone.

- if someone asks a question and the answer already exists, direct them to the documentation. Important: don't be a jerk about it. Furthermore, I often don't link directly to the document, but link to a hub document where that info is stored and tell the person where to find the exact link. This will require an extra click from the person, but it shows them the context of where the information exists. This improves the chances they can find something on their own later.

- simplify and clarify key documentation. Brevity and clarity are key to consumption. It's a skill. Do this iteratively.

- loudly and publicly celebrate people who make meaningful documentation contributions.

- when someone shares that they are leaving, make documenting their primary job for the remainder of their stay. If you tell them to finish their work, they may be successful or not. In either way, someone else will need to either finish the work, or maintain it. If you tell them focus on documenting, this will enable others to finish or support the work better. It's more leveraged.

- when someone goes on vacation, ask them to document some part of their work so that people don't call them on vacation. It's a good motivator to not to be called on vacation.

- hyperlink. Search and navigation are the primary ways of discovering knowledge. Search is limited to a single platform or system, and does not always work well. Hyperlinking allow you to associate information in time, space, relationship, which allows you to use common sense and navigate the knowledge graph.
weirik • on Feb 18, 2022
I experienced the exact same problem when I ran my web agency. So much so that I decided to quit after 20 years and start an insight management company instead (https://wecomplish.no/).
I belive that effectively collecting, sharing and reusing insight within any team requires culture, skills, tools, time and incentives.

## Culture/mindset Helping your team understand the value of managing insight is central in order to have everyone contributing effectively.

Recommended reading for you and your team:

* Insight management (https://wecomplish.no/article/insight-management) * Team playbook (https://wecomplish.no/article/team-playbook) * Fix organizational bugs (https://wecomplish.no/article/fix-organizational-bugs)

## A system/structure/taxonomy When you have the culture in place, you need to have a well suited location for storing and sharing insight.

I am of course biased towards the Wecomplish platform (https://wecomplish.no/platform) here, but I belive (like you) that the most important thing is to have a clearly defined structure/framework.

The structure of the Wecomplish platform is refined over 20 years and can be found here: https://app.wecomplish.no/overview

I belive this structure could be replicated in any insight management system.

## Skills If people don't understand which types of insight the team considers valuable, nor has the ability to distinguish between them, they will be held back.

The quick fix for this is to have a catch-all Wiki section where anyone is allowed to put anything, and where more experienced team members can refine and move stuff to the proper location at a later date.

The long terms solution is to improve the understanding of the differences between concepts like roles, responsibilities, processes, checklists, polices, etc.

For our clients, this is usually done through consulting servicess, but basically I belive this just takes time and practice.

Printing out and looking at https://app.wecomplish.no/overview might be a good place to start here.

## Time and incentives If a team always favours _doing_ work over _documenting_ or _improving_ work, there will never be time nor incentives to manage insight.

Make sure that insight sharing is clearly visible and celebrated within the team on the same level as deliveries in order to slowly but surely build up an insight management culture over time.

Good luck!
TheRealNGenius • on Feb 18, 2022
company's

# References

[^Brooks]: Ethan Brooks, _How To Write Stuff No One Else Can_, Published 2024-02-09, [[Online]](https://thewritetoroam.com/2024/02/how-to-write-stuff-no-one-else-can)

[^Quarto]: Quarto Maintainers, _Creating a Book_, Accessed 2024-02-19, [[Online]](https://quarto.org/docs/books/)

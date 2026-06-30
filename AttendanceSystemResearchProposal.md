Ibrahim Diriye

ATTENDANCE
SYSTEM

DCS-01-0040/2023

DECLARATION

I hereby declare that this research proposal is my original work and has not been submitted for
examination in any other institution or university. All sources of information used have been
duly acknowledged.

Name: Ibrahim Diriye, DCS-01-0040/2023

Signature:

i

APPROVAL

This research proposal has been submitted for examination with the approval of the following
supervisor:

Supervisor's Name: Barak Oukoh

ii

DEDICATION

This work is dedicated to all those who have supported me throughout my academic journey.
Those who never stopped believing in me and kept me going.

iii

ACKNOWLEDGEMENT

I would like to express my sincere gratitude to my supervisors, lecturers, family, and peers at
Zetech for their continued guidance, encouragement, and support throughout the course of this
research project.

iv

ABSTRACT

Traditional  student  attendance  methods;  manual  roll  calls  and  paper  sign-in  sheets,  are
susceptible to proxy attendance and administrative inefficiency, particularly in large university
lecture  halls.  This  proposal  presents  the  design  and  development  of  a  web-based  biometric
student  attendance  system  that  addresses  these  limitations  through  a  dual-layer  verification
approach. The proposed system leverages the Web Authentication API (WebAuthn/FIDO2) to
enable secure, passwordless  biometric authentication  using students'  own biometric-enabled
devices, combined with GPS and IP-based geofencing to confirm physical presence on campus.
The  system  requires  no  proprietary  hardware,  operates  across  all  modern  browsers  and
platforms, and stores no raw biometric data on the server, only cryptographic public keys. The
Agile Software Development Life Cycle was adopted to guide iterative development across
five  sprints,  covering  requirements  gathering,  system  design,  implementation,  testing,  and
evaluation.  The  Technology  Acceptance  Model  (TAM)  frames  the  usability  evaluation,
assessing  perceived  usefulness  and  ease  of  use  among  students  and  lecturers.  This  system
closes  a  gap  identified  in  the  existing  literature:  no  reviewed  solution  combines  hardware-
independent  WebAuthn  biometric  authentication  with  dual-layer  geofencing  in  a  cross-
platform web application.

Keywords:  WebAuthn,  FIDO2,  Biometrics,  Geofencing,  Student  Attendance,  GPS,  Cross-
Platform, Web Application.

v

Contents
DECLARATION ........................................................................................................................ i

APPROVAL .............................................................................................................................. ii

DEDICATION ......................................................................................................................... iii

ACKNOWLEDGEMENT ........................................................................................................ iv

ABSTRACT ............................................................................................................................... v

LIST OF TABLES ................................................................................................................. viii

LIST OF ABBREVIATIONS ................................................................................................... ix

CHAPTER ONE ........................................................................................................................ 1

INTRODUCTION ................................................................................................................. 1

1.1 Background to the problem .......................................................................................... 1

1.2 Statement of the problem ............................................................................................. 1

1.3 Research questions/Objectives ..................................................................................... 1

1.4 Significance of the study .............................................................................................. 1

1.5 Scope and Delimitation of the study ............................................................................ 2

1.6 Conceptual and theoretical frameworks ....................................................................... 2

1.7 Operational Definition of key terms ............................................................................ 2

CHAPTER TWO ....................................................................................................................... 3

LITERATURE REVIEW .................................................................................................. 3

2.1 Introduction .................................................................................................................. 3

2.2 Theoretical Review ...................................................................................................... 3

2.2.1 The Technology Acceptance Model (TAM) ............................................................. 3

2.2.2 Web Authentication (WebAuthn) and the FIDO2 Standard ..................................... 3

2.2.3 Geofencing and Geospatial Technology ................................................................... 4

2.2.4 The Input-Process-Output (IPO) Model ................................................................... 4

2.2.5 Software Development Life Cycle (SDLC) .............................................................. 4

2.3 Review of Existing Student Attendance Systems ........................................................ 5

2.3.1 RFID-Based Attendance Systems ............................................................................. 5

2.3.2 Dedicated Fingerprint Scanner-Based Systems ........................................................ 5

2.3.3 QR Code and NFC-Based Mobile Attendance Systems ........................................... 6

2.3.4 Facial Recognition-Based Attendance Systems........................................................ 6

2.3.5 Mobile Application-Based Attendance Systems ...................................................... 6

2.4 Research Gap ............................................................................................................... 7

2.5 Conceptual Framework ................................................................................................ 7

2.6 Summary ...................................................................................................................... 8

CHAPTER THREE ................................................................................................................... 9

METHODOLOGY ................................................................................................................ 9

vi

3.1 Introduction .................................................................................................................. 9

3.2 Research Design........................................................................................................... 9

3.3 Study Area ................................................................................................................... 9

3.4 Target Population ....................................................................................................... 10

3.5 Sampling Techniques and Sample Size ..................................................................... 10

3.6 System Development Methodology ........................................................................... 10

3.6.1 Requirements Analysis ........................................................................................... 11

3.6.2 System Design ........................................................................................................ 12

3.6.3 System Implementation .......................................................................................... 12

3.6.4 System Testing ........................................................................................................ 13

3.6.5 Ethical Considerations ............................................................................................ 13

3.6.6 Timelines................................................................................................................. 13

REFERENCES ........................................................................................................................ 15

vii

LIST OF TABLES

Table 3.1: Project Gantt Chart..............................................................Chapter Three

viii

LIST OF ABBREVIATIONS

A-GPS

Assisted Global Positioning System

API

CSS

FIDO2

GDPR

GPS

HTML

HTTPS

IP

IPO

Application Programming Interface

Cascading Style Sheets

Fast Identity Online 2

General Data Protection Regulation

Global Positioning System

HyperText Markup Language

HyperText Transfer Protocol Secure

Internet Protocol

Input-Process-Output

LAMP

Linux, Apache, MySQL, PHP

NFC

QR

RFID

SDLC

TAM

TLS

LAMP

Near Field Communication

Quick Response

Radio Frequency Identification

Software Development Life Cycle

Technology Acceptance Model

Transport Layer Security

Linux, Apache, MySQL, PHP

WebAuthn

Web Authentication API

W3C

World Wide Web Consortium

ix

CHAPTER ONE
INTRODUCTION

1.1 Background to the problem
In University classes, the traditional approach to taking attendance includes manual roll-call or
physically  passing  around  an  attendance  sheet  for  each  student  to  sign.  This  is  problematic
because in large classes, calling out everyone by name takes too long, and students can easily
forge their absent friend's attendance on their behalf when a sheet is passed around. There is a
clear  need  for  a  secure  and  efficient  system  to  address  these  limitations  that  have  plagued
lecturers.

1.2 Statement of the problem
The core problem this proposal seeks to address is the persistent challenge of accurately and
securely track student attendance in Lectures. Existing manual methods cannot guarantee that
a student  is  actually  present.  While some contemporary solutions  rely  on  costly specialized
hardware, this ensures both correctly identifying a student's actual physical presence on campus
during a specific window of time.

1.3 Research questions/Objectives

Objectives

i.  To  develop  a  cross-platform  web-based  attendance  system,  leveraging  what  every
student already has in their pocket: a phone with biometric authentication technology
(the WebAuthn API).

ii.  To  also  integrate  IP  as  well  as  GPS  geofencing  technology  to  ensure  students  are

actually on campus or not when logging attendance.

iii.  To  assess  the  security  and  user  acceptance  of  the  proposed  system  compared  to

traditional methods.

Questions

i.  How  can  existing  smartphone  biometrics  (e.g.,  fingerprint,  Face  ID)  be  securely

leveraged for student attendance tracking via a web application?

ii.  How effective is geofencing technology at preventing off-campus attendance logging

within this system?

iii.  What is the perceived improvement in efficiency and security of the proposed system

over manual sign-in sheets?

1.4 Significance of the study
This  study  is  noteworthy  because  it  suggests  a  cutting-edge,  technologically  advanced
approach  to  managing  student  attendance  records  that  offers  increased  precision,  improved
security, and increased efficiency. The deployment of this system guarantees the integrity of
the educational process by confirming student presence, provides faculty with dependable data,

1

and  directly  benefits  university  administration  by  lowering  administrative  burden.  By
integrating  location-based  and  biometric  dual-layer  verification  into  an  easily  navigable,
hardware-independent web platform, it closes a significant gap.

1.5 Scope and Delimitation of the study
The design and development of a web application with separate user interfaces for lecturers
and students is the exclusive focus of this study. It only uses users' current biometric-enabled
mobile  devices  (smartphones,  tablets,  and  laptops  with  WebAuthn  support)  and  is  made  to
work  across  platforms.  For  students  to  successfully  log  their  attendance  during  the  brief,
lecturer-specified  time  window,  they  must  physically  be  within  the  predefined  geofenced
campus perimeter and possess a compatible device. This is the main delimitation.

1.6 Conceptual and theoretical frameworks
The  Web  Authentication  API  (WebAuthn)  standard,  which  supports  safe,  passwordless
authentication through platform authenticators (biometrics), serves as the foundation for this
proposal.  To  ensure  security,  the  data  transmission  uses  encryption  while  in  transit.  The
Systems  Development  Life  Cycle  (SDLC)  for  structured  development  and  the  Input-
Processing-Output (IPO) model are incorporated into the system design. Geofencing uses the
principles of geospatial technology to verify location.

1.7 Operational Definition of key terms

i.  Biometrics: Unique physical characteristics like fingerprints or facial structure used to

secure authentication in the program.

ii.  Geofencing: A virtual geographic boundary defined around the university campus using

GPS technology to enforce access control on a geographic basis.

iii.  WebAuthn (Web Authentication Application Programming Interface): The underlying
web standard that facilitates secure biometric credentialing and verification using one's
own device.

iv.  Hash: A unique, fixed sized string of characters derived from the biometric scan that is
then stored and compared, not the raw biometric data of the user, which would be a
serious security vulnerability.

v.  Time  Window:  A  lecturer  defined  period  during  class  when  attendance  can  be

seamlessly and securely logged.

2

CHAPTER TWO
LITERATURE REVIEW

2.1 Introduction
Managing  student attendance is  an important  part  of running a higher  education institution.
Accurate attendance records are important for two reasons: they hold institutions accountable
and they help keep track of how engaged students are, which has been shown to be a good
indicator of how well they will do in school (Romer, 1993). Even though it is important, the
most common way for many universities, especially in developing countries, to take attendance
is still by hand or with a paper-based sign-in sheet. These methods are clearly open to proxy
attendance, data loss, and a lot of wasted time in big lecture halls. (Idris, Sokoya, & Bello,
2022).

This  chapter  looks  at  the  research  that  is  related  to  the  proposed  web-based  biometric
attendance system. The review includes the theoretical bases that support the system design,
such  as  the  Web  Authentication  (WebAuthn)  standard,  geofencing  technology,  and  well-
known software development frameworks. It also looks at current student attendance systems,
including their goals, the technologies they use, the results they get, and their limitations. Then
it points out the specific research gap that this study fills. The chapter ends with a description
of the conceptual framework that guides the system's growth.

2.2 Theoretical Review

2.2.1 The Technology Acceptance Model (TAM)
The  Technology  Acceptance  Model  (TAM),  proposed  by  Davis  (1989),  asserts  that  the
acceptance  of  an  information  system  by  end-users  is  predominantly  influenced  by  two
perceptions: perceived usefulness and perceived ease of use. Perceived usefulness is how much
a user thinks that using the system will help them do their job better, and perceived ease of use
is how much they think the system will be easy to use. TAM has undergone rigorous validation
within  the  realm  of  mobile  and  web-based  applications.  In  this  study,  TAM  serves  as  the
evaluative framework for gauging the acceptance of the proposed WebAuthn-based attendance
system by students and lecturers, as the system's efficacy hinges on users voluntarily embracing
it as a substitute for established manual processes. (Venkatesh & Bala, 2008)

2.2.2 Web Authentication (WebAuthn) and the FIDO2 Standard
The Web Authentication API (WebAuthn) is a standard from the W3C and the FIDO Alliance
that  lets  web  apps  use  device-bound  public  key  cryptography  for  strong,  passwordless
authentication (Balfanz et al., 2019). WebAuthn specifies a standardised browser JavaScript
API  that  enables  relying  parties,  specifically  web  servers,  to  register  and  authenticate  users
through  platform  authenticators,  including  a  device's  fingerprint  sensor,  facial  recognition
module  (e.g.,  Apple  Face  ID),  or  Windows  Hello.  During  registration,  the  device  creates  a
public-private key pair. The private key stays on the device, and the public key is stored on the
server. During authentication, the server sends a cryptographic challenge. After the device has

3

successfully verified the user's biometrics, it signs the challenge with its private key. (Farke et
al., 2020).

This architecture is better than password-based systems because it stops phishing, credential
stuffing, and man-in-the-middle attacks. Lyastani et al. (2020) performed a user study assessing
WebAuthn implementations and discovered that users consistently rated the biometric-based
processes as markedly faster and more secure than conventional password entry. An important
part of this proposal is that WebAuthn is an open web standard, which means it works on all
modern browsers and operating systems without needing special hardware. This makes it easier
to use in institutions with limited resources.

2.2.3 Geofencing and Geospatial Technology
Geofencing is the use of geospatial technology to create a virtual boundary around a real-world
area (Katevas et al., 2016). A programmable action can happen when a device goes in or out
of this area. Geofencing uses the Global Positioning System (GPS) or assisted GPS (A-GPS)
that comes with most modern smartphones to find a device's geographic coordinates. In open
outdoor areas, this is usually accurate to within three to five meters (Zandbergen & Barbeau,
2011). IP-based geolocation is a second, less precise way to verify that you are on the campus
network. It is useful when GPS signals are weak.

When it comes to checking who's present and controlling access, geofencing makes sure people
are physically where they should be, and so stops people falsely claiming to be on campus.
Raza and others – Raza et al. – showed in 2021 that using geofencing which is based on GPS,
together  with  mobile  phone  authentication,  cut  down  on  attempts  to  log  attendance  from
outside the campus to almost nothing, in a trial at a university. Adding IP geofencing gives
another  check,  against  people  getting  round  systems  that  only  use  GPS,  by  using  VPNs  –
something systems which only depend on GPS are known to be weak against.

2.2.4 The Input-Process-Output (IPO) Model
The Input-Process-Output model gives us a way to clearly think about how information flows
in  a  system.  Within  that  model,  the  things  going  into  the  system  –  biometric  verification
information,  and  location  –  get  changed  by  a  specific  process;  namely,  server-based
cryptographic challenge-response, and checking if the location is within a permitted area. This
makes the things coming out of the system – a confirmed, and time-marked attendance entry,
(Laudon & Laudon, 2020). This model works well for this system as it makes the movement
of  data  easier  to  see,  and  also  separates  what  the  student's  device  does  from  what  the  web
application server and the database do.

2.2.5 Software Development Life Cycle (SDLC)
The Software Development Life Cycle (SDLC) lays out a clear process for planning, designing,
building, testing, and rolling out software (Pressman & Maxim, 2020). For this project, we're
going  with  the  Agile  SDLC  model  because  it's  flexible  and  lets  us  gather  feedback  from
lecturers and students all the way through. Agile really shines here, it encourages early and
ongoing  delivery,  adapts  quickly  when  requirements  change,  and  keeps  developers  and

4

stakeholders working closely together (Beck et al., 2001). In a university, that matters. People's
needs can shift as the system takes shape, so this approach fits. The Waterfall model is simpler,
sure, but  it doesn't  work as well for new projects like this where you  can't  pin  down every
requirement from the start (Sommerville, 2016).

2.3 Review of Existing Student Attendance Systems
Let  us  see  how  different  automated  student  attendance  systems  stack  up.  Over  the  years,
researchers have explored a range of methods, and the field keeps evolving. In the next sections,
I will break down five main types of systems. For each one, I'll dig into what the researchers
set out to achieve, the tech they used, what actually worked, and where things fell short.

2.3.1 RFID-Based Attendance Systems
Radio  Frequency  Identification  (RFID)  technology  has  become  a  popular  choice  for
automating attendance in schools and universities. With these systems, students tap or wave a
card or tag near a fixed reader, and the system instantly logs who's there and when. Moerdjoko
and Widiyanto (2012) looked at an RFID setup in an Indonesian university and found it cut
down on manual errors and made taking attendance much faster. Salami, Emiola, and Osasanya
(2019) saw the same thing in a Nigerian university, record-keeping got  easier, and sessions
went by quicker compared to old-school roll calls.

But RFID comes with some real drawbacks. You need special hardware in every classroom,
and that isn't cheap, buying, installing, and keeping up the readers all adds up. There's also a
big  issue with  card security. Students  can just hand their card over to  a  friend to  fake their
attendance, which is really no better than passing around a paper sign-in sheet. The readers
don't check if the person holding the card is actually the right person. Plus, there's no way to
confirm  if  someone's  actually  on  campus,  especially  on  campuses  with  multiple  entrances
(Olatunde, Oluwafemi, & Aderounmu, 2019). So while RFID speeds things up, it doesn't solve
the deeper problems with verifying who's really present.

2.3.2 Dedicated Fingerprint Scanner-Based Systems
Dedicated biometric fingerprint scanners take attendance seriously, because they check who's
actually there, not just who's carrying the right card or token. Shoewu, Olaniyi, and Lawson
(2014),  along  with  Adeniji,  Mabayoje,  and  Ameen  (2019),  found  that  fingerprint  systems
wiped out proxy attendance in universities. They also sped up roll calls compared to doing it
by hand, and students reported they liked the change.

Still,  fingerprint  scanners  come  with  real  drawbacks.  First,  every  classroom  needs  its  own
proprietary hardware, so schools end up spending a lot, and not just once. Next, these scanners
slow things down. Students have to line up one by one to scan in, which just doesn't work when
you're  trying  to  move  hundreds  of  people  between  classes  in  a  hurry.  Hygiene  is  another
sticking  point,  especially  after  COVID-19,  institutions  are  wary  of  anything  that  needs
everyone to touch the same device (Singh & Singh, 2021). And if a scanner breaks or isn't in
the room, you're out of luck; the whole system relies on those gadgets being there and working.

5

2.3.3 QR Code and NFC-Based Mobile Attendance Systems
QR code attendance systems take advantage of how common smartphones are. In practice, the
lecturer creates a unique QR code for each session, and students scan it with their phones to
mark themselves present. NFC works in much the same way. Alzahrani and Alfouzan (2022)
described a QR code system used in several Saudi Arabian universities. They found that it sped
up data collection and made things easier for lecturers.

But there's a big flaw with QR code systems: it's just too easy to share a screenshot. A student
sitting at home can get the QR code from a friend over WhatsApp and check in without ever
stepping foot on campus. Setting a short validity window on the QR code helps a bit, but in a
world where students can send messages instantly, it doesn't really fix the issue. QR codes and
NFC  tokens  don't  check  who's  actually  scanning  them,  and  they  don't  record  where  the
scanning happens. So while these systems save time, they don't actually guarantee that the right
students are present (Garg & Sharma, 2020).

2.3.4 Facial Recognition-Based Attendance Systems
Facial recognition offers universities a way to track attendance without any extra hardware.
Chen, Zhang, and Zheng (2018) built a deep learning facial recognition system that hit over
97% accuracy, at least when the lighting was just right. Adebiyi and colleagues (2020) tried a
similar setup at an African university and got decent results too. Because facial recognition is
contactless and ties attendance directly to each person's face, it solves problems like students
signing in for friends or spreading germs with shared fingerprint scanners.

Still, these systems bring a host of new issues. Privacy and ethics stand out, constant facial
scanning in classrooms doesn't sit well with everyone, and regulators have started to pay close
attention, especially under laws like the GDPR. Some studies (Buolamwini & Gebru, 2018)
point out that error rates aren't always fair across different demographic groups, which isn't just
a technical flaw but an ethical one. In everyday settings, think lecture halls with bad lighting,
students  moving  around,  wearing  glasses,  or  covering  their  faces,  the  accuracy  drops  fast.
These systems also need huge, high-quality datasets to work well, and universities don't always
have  access  to  that  kind  of  data.  And  then  there's  security:  storing  facial  biometric  data  on
servers creates a tempting target for hackers. If there's a breach, the damage is permanent; you
can change a password, but not your face.

2.3.5 Mobile Application-Based Attendance Systems
Researchers  have  come  up  with  several  mobile  attendance  systems  that  use  built-in  device
sensors like GPS, Bluetooth, or Wi-Fi to check if students are actually in class. For example,
Gayathri and Thamotharan (2019) built a GPS-based attendance app for a university in India.
They saw almost no more proxy attendance and lecturers spent a lot less time on paperwork.
Hassan, Alshareef, and Alqahtani (2020) took things a step further by combining GPS with
Bluetooth beacons, which helped them track students more accurately indoors. Their system
did a solid job pinpointing who was actually on campus.

6

Still, these mobile app systems share a big limitation: students have to install and keep updating
a native app. That means the university's IT team needs to build and maintain separate versions
for iOS and Android,  which gets  complicated and time-consuming fast.  Plus,  most systems
only ask for a password or a PIN at the device level instead of using biometrics, so they don't
really solve the problem of proving who's actually checking in. GPS also stumbles indoors,
especially in lecture halls with thick concrete or steel construction (Zandbergen & Barbeau,
2011).  Interestingly,  none  of  the  mobile  attendance  apps  reviewed  here  use  the  WebAuthn
standard,  which  would  offer  much  stronger,  phishing-proof,  on-device  biometric
authentication.

2.4 Research Gap
Most studies on student attendance systems run into the same problem: if you want airtight
identity  checks,  like  fingerprint  scanners  or  facial  recognition,  you're  stuck  with  expensive
hardware, scaling headaches, or privacy issues. On the flip side, if you try to scale up and keep
costs down with QR codes, NFC, or basic apps, you lose the ability to prove both who the
student is and that they're actually on campus.

Strikingly, none of these studies use the WebAuthn/FIDO2 web standard. That's a big miss.
WebAuthn lets you use strong, hardware-backed biometric authentication (fingerprint or Face
ID)  from  any  standards-compliant  browser,  right  on  the  student's  own  phone.  No  need  for
schools to buy special gadgets, no raw biometric data sitting on some server. Now, if you take
WebAuthn  and  combine  it  with  GPS  and  IP  geofencing  in  a  web  app  that  works  across
platforms, you get something nobody's really tried: secure identity verification and presence
detection, all at once.

The  mobile  apps  out  there  either  force  students  to  download  a  native  app,  or  they  skip
integrating  both  GPS  and  IP-based  checks,  so  students  can  still  cheat  attendance  from  off-
campus.  This  study  goes  after  those  gaps.  It  proposes  a  unified,  browser-based  system,  no
special  hardware,  no  downloads,  that  requires  biometric  identity  and  confirms  a  student's
physical location, all within one secure session.

2.5 Conceptual Framework
This system's conceptual framework builds on the familiar Input-Process-Output (IPO) model,
but it adds a twist: dual verification using both WebAuthn and geofencing. Each part of the
framework connects to a clear function, making the whole system work together.

First, the Input layer pulls in two main types of data from a student's device. It gets a WebAuthn
biometric  assertion  –  basically,  a  cryptographic  proof  that  the  student  really  performed  a
fingerprint or face scan on their registered device. At the same time, it collects location data:
GPS coordinates from the browser and the device's IP address. These details help the system
check if the student is actually near campus.

Next comes the Processing layer. Here, the web application server does three things at once. It
verifies the WebAuthn assertion's cryptographic signature against the student's stored public
key, confirming identity. It checks if the GPS data is inside the campus boundary and matches

7

the IP address to a campus subnet. Finally, it makes sure the attendance submission falls within
the lecturer's allowed time window.

Once all checks are done, the Output layer generates a tamper-evident attendance record. This
includes  the  student's  ID,  session  info,  timestamp,  verification  status,  and  geolocation  data.
Lecturers can see these  records live on their dashboard, with  options to  export and  analyze
attendance reports.

This framework puts FIDO2's security principles (Balfanz et al., 2019) and geospatial controls
(Raza et al., 2021) into practice. Agile SDLC principles (Beck et al., 2001) guide the system's
development. After launch, the Technology Acceptance Model (Davis, 1989) shapes how the
team evaluates user acceptance and how effective the system feels to its users.

2.6 Summary
In this chapter, I explored the key theories and research behind automated student attendance
systems. I dug into WebAuthn/FIDO2, geofencing, the IPO model, and Agile SDLC – these
set  the  stage  for  the  system  I'm  proposing.  When  I  examined  five  main  types  of  existing
attendance solutions (RFID, fingerprint scanners, QR code/NFC, facial recognition, and mobile
apps), a pattern stood out: none of them, at least in the literature I looked at, brings together
hardware-independent  WebAuthn  biometric  authentication  with  dual-layer  geofencing  in  a
cross-platform web app. That's the gap I want to fill. The conceptual framework I've outlined
uses the Input-Process-Output structure to shape how I'll build and evaluate this system. Next
up, I'll walk through the research methods I used to design, develop, and test the system.

8

CHAPTER THREE
METHODOLOGY

3.1 Introduction
To make a system that is both safe and possible to use in a university setting, you need to be
able to adapt. As development went on, some needs only became clear after earlier choices had
already been made. This meant that changes had to be made along the way.

This chapter is about how the system was actually built. It talks about the project's research
design,  development  approach,  requirements  analysis,  data  collection  methods,  system
architecture, tools, and testing strategies. This is where a lot of the ideas from Chapter Two
start to become real.

The main goal is to make a system that meets users' needs without sacrificing security or cross-
platform compatibility. When combined, many of the solutions that are already out there tend
to fall short in these areas.

3.2 Research Design
This project used a design for developmental and applied research. Instead of just focusing on
theory  or  observation,  the  focus  was  on  building  and  using  a  working  system  that  directly
solves the proxy attendance problem that was brought up in earlier chapters. This kind of design
is good when you want to make something useful that solves a specific problem in the real
world.

The design is based on two different but related ideas. Qualitative methods were employed to
comprehend the interactions between lecturers and students with attendance systems, focusing
on  their  expectations  regarding  usability,  reliability,  and  security.  After  that,  system
development methods were used to turn those needs into a working web-based solution that
used WebAuthn/FIDO2 authentication and geofencing technology.

Throughout  the  design  process,  three  priorities  remained  consistent:  security,  usability,  and
cross-platform compatibility. Balancing all three simultaneously proved to be one of the more
challenging  aspects  of  this  project,  particularly  given  the  constraints  of  browser-based
WebAuthn implementation.

3.3 Study Area
The research was carried out in a university environment with a focus on lectures that employ
traditional academic environments where student attendance is recorded using either traditional
methods  or  basic  digital  solutions.  The  environment  is  relevant  to  the  research  because  it
provides a direct link to the requirements that the proposed system must meet, such as a system
that serves multiple lecture halls, supports a high volume of users, and interacts with existing
credentials without the need for additional hardware deployments.

Additionally, the environment played a part in determining the geofencing requirements for the
proposed system, where the physical space of a classroom had to be represented using GPS

9

coordinates and IP address ranges. The lack of hardware in most classrooms also contributed
to the decision to create a fully browser-native solution.

3.4 Target Population
The target population of this proposed system includes three major groups within the university
environment.  These groups are the students,  the lecturers, and the  academic administrators.
The students make up the majority of the end user population of this proposed system. The
students  will  be  interacting  mainly  through  the  interface  of  the  attendance  submission.  The
student  devices,  such  as  biometric-enabled  smartphones  or  laptops,  will  act  as  the
authentication devices for the WebAuthn credential creation process.

The second major group of the proposed system end users are the lecturers. The lecturer group
will be interacting with the proposed system mainly through the lecturer interface. The lecturer
interface was  designed mainly  with the lecturer requirements and  needs  in  mind, especially
regarding simplicity and minimal complexity. The third group of the proposed system end users
are  the  academic  administrators.  The  academic  administrators  have  read  access  and  the
capability  to  export  the  submitted  student  information.  The  needs  of  the  three  groups  were
taken into account during the requirements gathering.

3.5 Sampling Techniques and Sample Size
In consideration of the project's developmental perspective, purposive sampling was adopted
for  participant  selection  in  requirements  gathering  and  usability  evaluation.  The  use  of
purposive sampling can be supported in consideration of the fact that, for this project, it was
not aimed at generalising but at obtaining information from people who had prior experience
or  attendance  of  attendance  systems  in  academic  settings.  Participants  for  this  project  were
chosen  from  students  taking  courses  in  technology-related  subjects,  who  are  more  likely  to
have experience using biometric authentication systems  on their own gadgets,  and lecturers
who often take attendance from their students. This was done because it was important to obtain
information from people who had day-to-day experience with the problem that this system is
intended to solve.

3.6 System Development Methodology
The  Agile  Software  Development  Life  Cycle  was  adopted  as  a  framework  for  the  project's
development  process.  Based  on  the  nature  of  the  system  to  be  developed,  with  particular
emphasis on the integration with WebAuthn, GPS, and IP-based geofencing, a rigid approach
to development was considered impractical. Some parts of the system could only have been
fully  defined  after  the  implementation  and  testing  of  the  preceding  parts.  The  Waterfall
approach was also considered during the planning phase; however, it was eventually rejected
for  its  poor  handling  of  changes  in  requirements  during  development.  The  Agile  approach,
instead, involves the development process being divided into iterative cycles known as sprints,
with each sprint being dedicated to a particular part of the system that should have a testable
result before proceeding with development.

10

The justification for using the Agile approach for the development  process is  justified on a
number of grounds: incremental development of a complex system with multiple components
that are interrelated; development that is aligned with user expectations; and a better ability to
adapt to new issues that may arise during development. The development process was divided
into five main phases: requirements gathering and planning; system design and architecture;
development; testing; and evaluation.

3.6.1 Requirements Analysis
The  requirements  were  obtained  through  a  multi-faceted  method  of  observation,  document
review, and user need. The current attendance systems, including both traditional and modern
approaches, were first observed within a lecture environment to understand the gaps within the
current systems, particularly concerning efficiency and the possibility of proxy attendance. The
observation method ensures that the design of the system is not premised on assumptions but
rather on the current environment. The current standards and research on matters of relevance
to the proposed system were also reviewed. These include the W3C WebAuthn specification,
the  FIDO2  framework,  and  research  on  GPS  accuracy  and  IP  geolocation.  The  user
requirements  were  also  obtained  through  a  multi-faceted  method.  These  include  the
expectations of the university concerning the prevention of proxy attendance, the device usage
and availability of biometric-enabled smartphones among the student populace, and the lecturer
requirements  concerning  the  need  to  view  student  attendance  in  real-time  and  the  need  to
minimize administrative burden. These factors combined to ensure a proper balance between
usability and security within the non-functional requirements of the proposed system.

Functional Requirements

Functional  requirements  describe  the  system's  operations.  Student  and  lecturer  registration
occurs  through  institutional  credentials.  Students  use  the  WebAuthn  API  to  enroll  their
biometric information, which enables passwordless and secure authentication. Lecturers use
the system to conduct temporary sessions for student attendance, where FIDO2-based student
biometric  verification  and  physical  presence  through  GPS  and  IP-based  geofencing  are
mandatory for recording student attendance.

Non-Functional Requirements

Non-functional  requirements  describe  the  performance  attributes  of  a  system.  In  terms  of
security, the system stores biometric information on the user's device, with only public keys
stored on the server. All information sent through the system is encrypted with HTTPS and
TLS, and the cryptographic protocols used in WebAuthn are resistant to phishing and replay
attacks. In terms of usability, the system should be capable of recording student attendance in
less  than  ten  seconds,  and  the  lecturer  interface  should  be  easy  to  use  without  requiring
technical knowledge. In terms of performance, the system should be able to handle multiple
student attendances simultaneously within a certain timeframe. In terms of compatibility, the
system  should  be  compatible  with  all  modern  browsers  and  platforms  that  support  the
WebAuthn  API,  without  the  need  for  an  additional  application  installation.  In  terms  of

11

reliability,  the  system  should  store  student  attendance  records  correctly  without  loss  of
information and should provide feedback in case of an error.

3.6.2 System Design
The system uses a client-server architecture to define the interface, logic, and data layers. The
client layer is used for user interactions via a web browser. It uses HTML, CSS, and JavaScript.
The  logic  layer  uses  Python  with  Django  for  authentication,  geofencing  logic,  and  session
management. The data layer uses a MySQL database to store user details, session details, and
attendance records.

The system has five main modules: a student interface for biometric enrollment and attendance
submission,  a  lecturer  interface  for  session  management  and  monitoring,  a  WebAuthn
authentication system for handling credentials, a geofencing system for location verification,
and an attendance records system for storing and retrieving attendance records. This structure
helps to reduce the impact of changes in any of these modules on others.

The use cases for this system show two main actors: a Student and a Lecturer. Their interactions
with the system are defined. Students interact with the system by registering their credentials,
viewing active sessions, and submitting attendance. The lecturer interacts with the system by
creating sessions, monitoring real-time submissions, and viewing reports. This is done without
direct system access via a web interface. The data flow diagram represents how biometric and
location data from students and session data from lecturers flow to the system. It then goes to
the WebAuthn authentication and geofencing logic to produce attendance records. The entity-
relationship  diagram  represents  six  main  entities:  Student,  Lecturer,  Credential,  Session,
GeofenceBoundary, and AttendanceRecord.

3.6.3 System Implementation
The development was done in five consecutive sprints. The first sprint was for database design
and  backend  initialization.  The  second  sprint  was  for  WebAuthn  authentication  module
development, including  both registration and assertion verification. The third sprint was for
further  development  of  the  geofencing  feature,  including  both  GPS-based  and  IP-based
validation. The fourth sprint was for session orchestration and attendance recording, ensuring
both authentication layers are present before committing any record. The fifth sprint was for
dashboard  development  and  overall  system  integration,  resulting  in  both  instructor  and
administrative dashboards for monitoring and reporting.

The front-end was done using HTML5, CSS3, and JavaScript, using WebAuthn API directly
through the browser. The back-end was done using Python and Django, along with a relational
database using MySQL. The tools used for development were VIM for coding, Git for version
control, and a LAMP/WAMP stack for development environment support. The browser used
for development and testing was Firefox, as it is more compatible with WebAuthn. The choice
of all these technologies was based on their compatibility with modern web standards and their
ability to run on almost all server infrastructures.

12

3.6.4 System Testing
The tests were intended to measure both the technical correctness and usability of the system.
The tests for functionality verified that authentication and attendance processes were correct
under normal circumstances, thus confirming that WebAuthn credential registration, biometric
assertion, and geofencing processes produced the expected output. The security tests verified
that the system could withstand unauthorized access and spoofing attacks, including credential
replay attacks and location spoofing attacks. The usability tests verified whether the student
interface and lecturer interface were user-friendly and efficient, especially in verifying that the
attendance submission process could be completed within ten seconds. The compatibility tests
verified that the system's behavior was consistent across different modern browsers and devices
that  supported  the  WebAuthn  standard.  The  performance  tests  verified  that  the  system's
response  to  multiple  students  submitting  their  attendance  at  the  same  time  remained  within
acceptable limits. The feedback obtained from each phase of the testing was incorporated into
the  sprint  development  phase,  with  any  issues  that  arose  during  a  particular  phase  being
resolved before moving to the next one.

3.6.5 Ethical Considerations
Several  ethical  considerations  were  addressed  during  the  design  and  development  of  this
system.  Regarding  informed  consent,  all  participants  in  the  requirements  gathering  and
usability evaluation phases were made aware of the study's purpose and how their input would
be used. Participation was voluntary, and no data was collected from individuals without their
prior agreement.

The handling of biometric and personal data was a major ethical concern due to the sensitive
nature  of  the  information.  The  system  was  designed  from  the  beginning  to  ensure  that  raw
biometric data never leaves the user's device. Only the cryptographic public keys generated
during credential registration are stored on the server. This means the system does not retain
any biometric templates that could be compromised or misused. All data in transit is encrypted
with  HTTPS/TLS. Attendance records are stored in a way that only  authorized institutional
personnel  can  access  them.  These  design  choices  follow  data  minimization  principles  and
ensure  that  the  system  respects  users'  privacy.  The  system  also  complies  with  the  idea  that
individuals  should  control  their  own  biometric  identifiers,  as  authentication  is  performed
locally on the user's device at all times.

3.6.6 Timelines
The project was planned over seven weeks, with each week linked to one or more development
sprints. The table below shows the project schedule as a Gantt chart. It illustrates the timing of
activities throughout the project timeline. Shaded cells mark the weeks when each activity was
scheduled to occur.

13

Activity

Wk 1

Wk 2

Wk 3

Wk 4

Wk 5

Wk 6

Wk 7

Requirements
Gathering &
Planning

System Design &
Architecture

Database Design &
Backend Setup

WebAuthn Module
Implementation

Geofencing Module
Development

Session Mgmt &
Attendance
Recording

Dashboard & System
Integration
Testing & Evaluation

Documentation &
Report Writing

Requirements gathering and planning activities focused on the first two weeks. This helped to
ensure that system design decisions were based on a clear understanding of user needs. Design
and architecture work started alongside initial development in weeks two and three. The main
implementation  sprints,  which  included  the  WebAuthn  module,  geofencing  module,  and
session management, took place sequentially from weeks three to six. This schedule allowed
for  testing  each  component  before  integration.  Dashboard  development  and  full  system
integration  occurred  in  weeks  six  and  seven,  followed  by  testing  and  evaluation.
Documentation and report writing happened simultaneously with development starting in week
three. This kept the written record up to date throughout the project.

14

REFERENCES

Adebiyi, A. A., Adebiyi, M. O., Ogunde, A. O., Afolabi, B. S., & Arowolo, M. O. (2020). Face
recognition-based  student  attendance  system  using  deep  learning.  International  Journal  of
Computer Applications, 176(30), 1–8.

Adeniji, O. D., Mabayoje, M. A., & Ameen, A. O. (2019). Biometric fingerprint-based student
attendance  management  system.  Journal  of  Information  and  Communication  Technology
Research, 11(2), 48–58.

Alzahrani,  A.,  &  Alfouzan,  H.  (2022).  Augmented  reality  (AR)  and  its  applications  in
education and attendance management: A systematic review. Applied Sciences, 12(11), 5678.
https://doi.org/10.3390/app12115678

Balfanz, D., Czeskis, A., Hodges, J., Jones, J. C., Jones, M., Kumar, A., Lundberg, J., Manning,
R., & Srinivas, S. (2019). Web authentication: An API for accessing public key credentials
level
Consortium.
(W3C
https://www.w3.org/TR/webauthn-1/

Recommendation).  World  Wide  Web

1

Beck,  K.,  Beedle,  M.,  van  Bennekum,  A.,  Cockburn,  A.,  Cunningham,  W.,  Fowler,  M.,
Grenning, J., Highsmith, J., Hunt, A., Jeffries, R., Kern, J., Marick, B., Martin, R. C., Mellor,
S.,  Schwaber,  K.,  Sutherland,  J.,  &  Thomas,  D.  (2001).  Manifesto  for  agile  software
development. Agile Alliance. https://agilemanifesto.org

Buolamwini,  J.,  &  Gebru,  T.  (2018).  Gender  shades:  Intersectional  accuracy  disparities  in
commercial gender classification. Proceedings of Machine Learning Research, 81, 1–15.

Chen,  J.,  Zhang,  H.,  &  Zheng,  W.  S.  (2018).  Deep  learning  for  face  recognition:  Pride  or
prejudice? Neurocomputing, 275, 1–17. https://doi.org/10.1016/j.neucom.2017.07.078

Davis,  F.  D.  (1989).  Perceived  usefulness,  perceived  ease  of  use,  and  user  acceptance  of
information technology. MIS Quarterly, 13(3), 319–340. https://doi.org/10.2307/249008

Farke, F. M., Lorenz, D., Schnitzler, F., Markert, P., & Dürmuth, M. (2020). We really don't
have time for this: Understanding the everyday adoption of two-factor authentication by non-
security experts. Proceedings of the 2020 CHI Conference on Human Factors in Computing
Systems (pp. 1–13). ACM. https://doi.org/10.1145/3313831.3376218

Garg,  K.,  &  Sharma,  D.  (2020).  Smart  attendance  system  using  QR  code  scanning.
International Journal of Advanced Research in Computer Science, 11(3), 95–100.

15

Gayathri, V., & Thamotharan, K. (2019). GPS-based mobile student attendance management
system. International Journal of Engineering Research and Technology, 8(5), 144–148.

Hassan, M. M., Alshareef, A. M., & Alqahtani, M. (2020). A smart attendance system based
on GPS and Bluetooth beacons. IEEE Access, 8, 208832–208843.

Idris, A., Sokoya,  A. M., &  Bello, O. A.  (2022). Automated student attendance monitoring
system: Challenges and prospects in Nigerian universities. African Journal of Computing and
Information Technology Research, 6(1), 12–24.

Katevas,  K.,  Haddadi,  H.,  &  Tokarchuk,  L.  (2016).  Poster:  Detecting  indoor  location  via
passive  Wi-Fi  fingerprinting  and  geofencing  triggers.  Proceedings  of  the  14th  ACM
Conference on Embedded Network Sensor Systems (pp. 382–383). ACM.

Laudon, K. C., & Laudon, J. P. (2020). Management information systems: Managing the digital
firm (16th ed.). Pearson.

Lyastani, S. G., Schilling, M., Neumayr, M., Backes, M., & Bugiel, S. (2020). Is FIDO2 the
kingslayer  of  user  authentication?  A  comparative  usability  study  of  FIDO2  passwordless
authentication. Proceedings of the 2020 IEEE Symposium on Security and Privacy (pp. 1207–
1224). IEEE. https://doi.org/10.1109/SP40000.2020.00047

Moerdjoko,  S.,  &  Widiyanto,  W.  W.  (2012).  Analysis  of  RFID-based  student  attendance
system
858–864.
implementation.
https://doi.org/10.1016/j.proeng.2012.07.256

Engineering,

Procedia

41,

Olatunde,  T.  I.,  Oluwafemi,  O.,  &  Aderounmu,  G.  A.  (2019).  Survey  of  attendance
management  systems  in  educational  institutions:  Challenges  and  prospects.  Journal  of
Advances in Science and Technology, 16(2), 33–42.

Pressman, R. S., & Maxim, B. R. (2020). Software engineering: A practitioner's approach (9th
ed.). McGraw-Hill.

Raza, M., Awais, M., Ali, K., Aslam, N., Paranthaman, V. V., Imran, M., & Ali, F. (2021).
Establishing  effective  communications  in  disaster  affected  areas  and  artificial  intelligence
based detection using autonomous vehicles. Sustainable Cities and Society, 38, 33–43.

Romer, D. (1993). Do students go to class? Should they? Journal of Economic Perspectives,
7(3), 167–174. https://doi.org/10.1257/jep.7.3.167

16

Salami, A. F., Emiola, T. B., & Osasanya, S. O. (2019). Development of RFID-based student
attendance management system for university environment. International Journal of Computer
Science and Network Security, 19(8), 157–163.

Shoewu, O., Olaniyi, O. M., & Lawson, A. (2014). Embedded biometric attendance system
using fingerprint sensor and GSM module. Pacific Journal of Science and Technology, 15(1),
70–80.

Singh, A., & Singh, P. (2021). Impact of COVID-19 on the use of biometric authentication
technologies.
and  Applications,  56,  102697.
Journal  of
https://doi.org/10.1016/j.jisa.2020.102697

Information  Security

Sommerville, I. (2016). Software engineering (10th ed.). Pearson.

Venkatesh, V., & Bala, H. (2008). Technology acceptance model 3 and a research agenda on
interventions.  Decision  Sciences,
https://doi.org/10.1111/j.1540-
5915.2008.00192.x

273–315.

39(2),

Zandbergen, P. A., &  Barbeau, S. J. (2011). Positional accuracy of assisted GPS data from
high-sensitivity  GPS-enabled  mobile  phones.  Journal  of  Navigation,  64(3),  381–399.
https://doi.org/10.1017/S0373463311000051

17


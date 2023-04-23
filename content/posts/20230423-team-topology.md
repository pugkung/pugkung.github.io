---
Title: "Team Topologies"
description: "Short desc"
featured_image: "/img/team_book_cover.jpg"
Publishdate: 2023-04-23
categories: ["Non-Technical", "Agile"]
tags: ["Agile", "Management", "Book"]
---

I have been trying to look for an optimal way to ensure that my working team is efficiently and which area could be improved or moving toward to. The book *"Team Topologies"* was being mentioned by my ex-boss and it caught my interest.

This post will be about a short summary of the book contents

<img src="/img/team_book_cover.jpg" width=280 height=400>
<br>

# Sections
- [Team Sizing](#team-size)
- [Type of Team Structures](#team-structures)
- [Type of Team Interactions](#team-interactions)
- [TLDR;](#tldr)
- [Closing](#closing)

## Team Size <a name="team-size"></a>
Generally team size **should be around 5-8 members** to avoid communication overload between members. 

Large teams or divisions may break down into sub-teams which can still share their skillset and expertise between teams.

Each team could be divided (and should be aligned with each other) by 
- Business Area
- Regulatory
- Physical Location 
- Technical Dependency
- Change Velocity


## Team Structures <a name="team-structures"></a>
Team are generally identified into 4 categories:
<table>
    <tr>
        <th>Type</th>
        <th>Role</th>
    </tr>
    <tr>
        <td>Steam-Aligned</td>
        <td><ul>
            <li>Common team tied to certain product or business</li>
        </ul></td>
    </tr>
    <tr>
        <td>Complicated Subsystem</td>
        <td><ul>
            <li>Specialist in certain field</li>
            <li>Maintain tightly coupled/legacy components</li>
        </ul></td>
    </tr>
    <tr>
        <td>Platform</td>
        <td><ul>
            <li>Offload underlying tasks for Stream-Aligned/Complicated Subsystem team</li>
            <li>Provide generic services to other team</li>
        </ul></td>
    </tr>
    <tr>
        <td>Enabling</td>
        <td><ul>
            <li>Support other teams to achieve their goals</li>
            <li>Discover and try to innovate how to improve workflow</li>
        </ul></td>
    </tr>
</table>

## Team Interactions <a name="team-interactions"></a>
The interaction between team are generally put into 3 categories:
- **Collaboration**
  - Two (or more) teams are working closely in a given time frame for solving certain problems. All teams shared their ownership/responsibility together as whole.
- **X-as-a-Service**
  - A team expose a certain way to interact with other team. Similar to how we sent request to API endpoint which require well-defined schema as input. Most interaction are predictable.
- **Facilitating**
  - An experienced team act as a mentor to another team to get over obstacles or encourage team to do something (eg. logging standard/agile coach/CICD)

<table>
    <tr>
        <th>Mode</th>
        <th>Pros</th>
        <th>Cons</th>
        <th>Example</th>
    </tr>
    <tr>
        <td>Collaboration</td>
        <td><ul>
            <li>Quick discovery</li>
        </ul></td>
        <td><ul>
            <li>Exhausting</li>
        </ul></td>
        <td><ul>
            <li>Platform↔Stream-Aligned</li>
            <li>Complicated Subsystem↔Stream-Aligned</li>
        </ul></td>
    </tr>
    <tr>
        <td>X-as-a-Service</td>
        <td><ul>
            <li>Well defined</li>
            <li>Lower cognitive load</li>
        </ul></td>
        <td><ul>
            <li>Slow innovation</li>
            <li>Lower consumer insight</li>
        </ul></td>
        <td><ul>
            <li>Platform↔Stream-Aligned</li>
            <li>Complicated Subsystem↔Stream-Aligned</li>
        </ul></td>
    </tr>
    <tr>
        <td>Facilitating</td>
        <td><ul>
            <li>Improve deliverable velocity/quality</li>
            <li>Further identify improvements</li>
        </ul></td>
        <td><ul>
            <li>Required experience from facilitating team</li>
        </ul></td>
        <td><ul>
            <li>Enabling↔Stream-Aligned</li>
        </ul></td>
    </tr>
</table>
The interaction mode are not meant to remain as-is forever. Teams will eventually change how to work together over time. For example:

- Collaborating teams established an communication agreement between teams (X-as-a-Service)
- Enabling team moved to facilitate another team


## TLDR; <a name="tldr"></a>
In summary, this book is meant for managers who are thriving to setup optimal team structure for software development which should be considered by team's type and how they should be interact each other
- ***Four fundamental teams***
  - **Stream-Aligned**: general team tied to product/service
  - **Complicated subsystem**: similar to steam-aligned, but maintain more complicated or legacy components
  - **Platform**: provide shared services for other teams
  - **Enabling**: expertise, but not tying to specific business area
- ***Three interaction modes***
  - **Collaborating**: initial state of discovery
  - **X-as-a-service**: goal for stable teams
  - **Facilitating**: to enforce or encourage something

## Closing <a name="closing"></a>
In the end, Team Topologies meant to be an optimal "template" for team management. It explains the "most likely" efficient team format that we should be, or moving to when we are growing into a hugh organization in a rational way. 

Wether how much it could be carry out is depend on the constraints and how team member willing to open-up with the changes. These stuff may not be directly mention on the book, but it is all about communication and transparency of leadership people. The more trust we have, the less friction would be regardless of hardship (i believe...)

For more detail, you can visit the author's website (https://teamtopologies.com/) and you could also get their copy of book which will contain more examples and further reading references.

I am currently reading another book that the author published *"Remote Team Interactions Workbook"* and I would make another post about what I have learnt from it.
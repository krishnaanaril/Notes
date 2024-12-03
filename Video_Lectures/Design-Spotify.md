# [Google system design interview: Design Spotify](https://www.youtube.com/watch?v=_K-eupuDVEc)

## Clarifying Questions
- Constrain the problem to make it solvable in an hour.
- Share what you know about the system to the interviewer.
- If you're not familiar, they can fill you in.

## Calculate the amount of data you're dealing with
- Users: 1 billion
- Songs: 100 million
- Song size: 5 MB

## Metrics
- Specify some key metrics to help your high level decision-making.
- In this case, the number of users and songs.
- You don't necessarily have to go into the details of scaling at this point.

## Layout the basic components of your design

## High Level
- Good dual bandwidth communication is important, so practice it.
- At an early stage, it's okay to have a few simple components
- Later on you can get more complex.

## Outline your database design
- After laying out your components, design your database.
- Split out databases appropriate for different types of data.
- Explain your decision-making proactively.

## Run through the usecase of finding music

## Drill down
- Talk through use cases to check your design and identify bottlenecks.
- Identify exisiting technologies such as CDNs for caching.
- Discusss how solutions such as caching apply at different levels in your solution.

## Load balancing
- Load balancing is not one size fits all.
- Consider multiple metrics when applying technologies such as load balancing.
- Be open about the limits of your expertise.

## Bring it all together
- Wrap up your answer by outlining how it meets the requirements
- End of interview is a chance to think big and introduce a new dimension.
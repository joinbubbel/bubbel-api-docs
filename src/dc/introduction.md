# Data Channel

What do text messages, posts, and even whiteboards have in common?
Well, it allows users to post pieces of data and have those pieces of data update for other users.

Yes, think about it, they all follow this behavior.
For this reason, we maintain one system for all of these use cases: the **Data Channel**.

Data channels are very simple.
You can:

1. send messages.
2. delete messages.
3. edit messages.

All connected clients are notified when an important event occurs.
Notifications are sent in real time without polling!

Messages are stored in **chunks** where each chunk stores a certain number of saved messages.


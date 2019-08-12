Week 5 marked the start of my second evaluation. The activities in week one proved more formidable than I thought.
Partly because of the fact that I was unable to spend long hours at an issue at hand, thereby reducing my efficiency.

Well no matter; a new week meant a new start and I was ready to take on more. I started off with the Chat-activity, implementing
the feature of Search, similar to one found in the Log-activity. The PR was not new to me, I had already done a fair amount of work
on it before the coding phase began.

My first task was to refactor most of the code. I realised that I had based it upon how search was done in Log-activity, but realised
that I has used many unnecessary features as well, such adding GLib.Timeout for every search and updating it on a new search. Plus the
function calls I was making seemed redundant. I simplied the function calls I had to make. I was using the same function to perform the task
of searching if their existed any further matches as well as find the next match. This, while it seemed to reduce code length, was causing
unexpected behaviour so I decided to separate them into two different functions.

Earlier I was making use of Gtk.TextIter to keep track of the present match, which was highlighted in cyan and the rest of the matches in red.
This was a fatal error, as I was not aware that Gtk.TextIter does not have persistence storage as the official docs say, _Iterators are not valid indefinitely;
whenever the buffer is modified in a way that affects the number of characters in the buffer, all outstanding iterators become invalid. 
Because of this, iterators can't be used to preserve positions across buffer modifications. To preserve a position, the GtkTextMark object is ideal_.

I decided to switch over to using Gtk.TextMark to preserve the location of the present match and update it as and when the previous and next buttons are clicked.
I was able to get it working, however I was yet to setup my collaboration testing environment and thus could not fully test the changes. My mentor Ibiam pointed out
what he felt was unexpected behaviour in the activity, and I shall describe how I worked on that in a later post.

The other activity that I began working on was the Maze-activity, where I was supposed to implement the feature of holes. Holes were merely obstacles that a user would need to
avoid inorder to reach the destination. Passing over a hole would essentially mean that you fall in one and the restart the game from start. This was by far the most fun I had in 
implementing the feature. Like Chat-activity, I had done most of the work before the coding phase and I decided to pick up from where I left. I however made the mistake of starting 
a new Pull Request, basing it on my earlier commits, for which I was reprimanded by my mentor. He felt that I should have continued to work on the same branch as it helped a maintainer
keep track of changes and the discussion.

I got my collaboration environment setup which was a pain itself, however following my mentor's suggestion of setting up Live Sugar builds, I finally got collaboration to work. I began testing Maze-activity
right away. I refactored most of the code (I just realised how much I refactor earlier code, especially after having gained experience working GTK based libraries). However, the feature was failing on collaboration
as the holes were not being shared correctly and if one player were to pass over it, the game would go off-sync. How I overcame this shall be a part of the next blog post.

Another feature I started working on was how to indicate connection progress during the time when Chat-activity connects to an already shared activity, much similar to how Maze-activity performed a similar task.
It was arelatively straight forward task, with a one line change, but took some time to test.

Links to PR from Week 5:
https://github.com/sugarlabs/chat/pull/19
https://github.com/sugarlabs/maze-activity/pull/30
https://github.com/sugarlabs/chat/pull/24
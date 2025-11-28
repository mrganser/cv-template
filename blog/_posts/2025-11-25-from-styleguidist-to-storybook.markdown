---
layout: post
title:  "The One where we migrated to Storybook"
author: "@mrganser"
---

As a Principal Software Engineer, one of my ongoing missions is to keep technical debt under control while introducing stable, modern technologies to my teams. In this case, Styleguidist was starting to fall behind as a UI development tool, while Storybook had already proven its stability and received consistent updates over time. I decided to lead this migration to give both the engineering and design departments a more reliable, feature-rich tool to manage our design system.

## Methodology

I like to approach large projects like this through vertical slices, applying refactoring strategies that support iterative progress and reduce the risk of the project stalling before completion.

We had a solid starting point, all our component documentation was already written in Markdown with examples. They could be better, but the goal was clear: transition that content into Storybook stories while keeping scope under control. Adding new examples or extra functionality could come later.

Another advantage was that there was no risk of breaking production code since this effort was just about documentation for our UI kit. At most, the migration could reveal component bugs, which would then be tracked separately.

## How-to

Here is how I broke it down. Every step could be shipped on its own, with zero risk or blockers waiting on the next one:

1. **Ensure all tests are present and green before refactoring**

   The implementation itself was not going to change, but having a solid test suite is always good practice. Fortunately, we were in a strong position here, so we already had them.

   **Outcome:** Confident that no hidden issues appear if implementation details need adjustment.

2. **Install Storybook**

   I just followed the latest Storybook documentation to complete the integration.

   **Outcome:** Able to run Storybook and display a basic example page.

3. **Migrate one component example to stories**

   Add a `component.stories.md` file alongside the existing component Markdown file with the stories for that component. Do not remove the old one yet, keep it until you are confident everything works as expected.

   **Outcome:** Understand how complex the migration is and what adjustments are required.

4. **Migrate the rest of the components**

   After the first one, the process is repeatable and safe. I actually used an AI agent to speed this up, using my first migrated component as an example. After a few tweaks, it proved to be a huge time saver.

   **Outcome:** The entire UI kit is now fully migrated and running in Storybook.

5. **Cleanup**

   Once everything is in place, it is time to remove the old Markdown files, the Styleguidist setup, and related dependencies.

   **Outcome:** Always be a good boy scout :)

6. **Queue up future work**

   The refactor is technically done, but when you touch this many things, it is common to uncover bugs, missing stories, missing tests, or even cool new Storybook features you want to explore. Resist the urge to fix everything right away, just take notes to handle them later. Also, the longer the refactor stays open, the more merge conflicts and headaches you create for the team.

   **Outcome:** Separate concerns, avoid mixing refactors with features, and save the extras for another day.

7. **Train the team with lessons learned**

   Show how you did it together with the basics about Storybook.

   **Outcome:** You want the team to be on the same page as you and able to expand the Storybook content without any problems.

## Conclusion

This migration was not just about swapping tools, it was about setting up a stronger foundation for our design system. Moving from Styleguidist to Storybook gave us a modern, actively maintained environment that is easier to scale and friendlier for both developers and designers.

The main takeaway? Keep refactors small. Focus on completing the transition first, then improve from there. Small, safe, and visible steps are always better than the big bang approach. With a clean setup, clear documentation, and a queue of follow ups ready to go, you are set for success. I have seen plenty of refactor projects fall apart just because they kept growing out of scope.

## Would you like to know more?

Check out the [Storybook docs][storybook-docs]{:target="_blank" rel="noopener noreferrer"} for more information.

[storybook-docs]: https://storybook.js.org/docs

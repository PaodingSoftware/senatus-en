# GitHub Spec-Kit is Just Too Complex

I spent some time trying out Spec-Kit on a personal project, and honestly, it wasn't for me.

Spec-Kit generates mountains of documentation for a single feature. Combined with AI's tendency to use terse, abstract language, reading through all this documentation became exhausting.

I tried powering through—skimming the docs with a sense of adventure before moving to the next phase. That didn't work. Spec-Kit's structure is like a funnel: each phase builds on the previous one's documentation, generating even more content. Any small error in the docs gets amplified in the next phase, eventually spiraling out of control. It's a butterfly effect.

The multi-phase structure also makes rollbacks expensive. Generally, the earlier you catch a problem, the easier it is to roll back and minimize damage. But problems often don't surface until the final stages.

In Vibe Coding, iterating on AI outputs is the norm. Spec-Kit doesn't seem to embrace this philosophy. It assumes the result after running `implement` should just work. If something's wrong, you're supposed to go back and fix the documentation. But in reality, most of your development time is spent on post-implementation tweaks and refinements. This is where Spec-Kit offers little help.

Spec-Kit also comes with a lot of built-in opinions: TDD, contracts, data models, and so on. I found myself adding counter-directives in the constitution to push back against these defaults, like: "don't generate excessive tests" or "don't generate contract files."

## So What Do I Actually Need?

Today's AI is capable enough to handle most development tasks. The real bottleneck is human expression. When I describe requirements to AI, I can usually only articulate about 20% of what's in my head. The rest is left for the AI to guess. That's why I've learned to have several rounds of conversation with AI before implementation—to excavate those hidden details through dialogue.

Another challenge is context window limits. These limits determine how complex a task AI can handle. When AI is forced to compress context, it forgets critical details. After a few rounds of this, everything becomes chaotic. To avoid this, I deliberately ask AI to distill our discussions into documentation that can be referenced later.

I've distilled these two key points into a simple phrase: "discuss and document."

## Senatus - My Own Design Philosophy

Inspired by Spec-Kit, I realized I could formalize these two principles into a standardized system. I call it Senatus. Like the painting below (yes, also AI-generated).

![Senatus Framework](../senatus.png)

### discuss.md

Senatus centers around a `discuss.md` file. Unlike `spec.md`, it doesn't have rigid sections. It looks something like this:

``` markdown
# Discussion Topics

Q: Should user login use JWT or sessions?
A: Given our decoupled frontend/backend architecture, JWT makes more sense. It's stateless, scales easily, and works well for mobile clients.

Q: For user avatars in the database, should we store the image path or the actual image?
A: Store the OSS path. Storing images directly would bloat the database and prevent CDN acceleration.

...
```

Simple, right?

Developers can use `/discuss` or `/inspire` commands to engage in discussion with AI. When the command finishes, AI appends the discussion results to `discuss.md`.

The only difference between `/discuss` and `/inspire`: when you're not sure what else to discuss, run `/inspire` and let AI suggest a topic for you.

### plan.md

When you feel you've discussed enough with AI, run `/plan` to generate a plan file based on `discuss.md`. The `plan.md` is equally straightforward:

``` markdown
# Task Plan

Task 1: Implement user registration, including email verification and password encryption
Task 2: Design and implement user login endpoint, returning JWT token
Task 3: Develop profile editing page with avatar upload support

...
```

Then you can use `/implement` to execute these tasks sequentially.

The beauty of a simple task plan is that you can roll back at any time. You can completely roll back all completed tasks, or keep what's done and have AI replan the remaining work.

### `/correct` and `/collect`

When tasks are complete, you'll inevitably find the results aren't quite right. That's when you use `/correct` for fine-tuning. After fixing things, `/correct` updates the adjustments back into `discuss.md` and `plan.md`.

Alternatively, you can make manual adjustments yourself, then use `/collect` to consolidate and sync those changes back to `plan.md`.

What matters is that `discuss.md` stays active throughout, capturing all the important details from the entire development process.

### Simple Enough?

That's all there is to Senatus. Simple, right? Yet surprisingly effective. The whole project doesn't rely on complex scripts—each command document is kept under 200-300 words, so you can quickly understand and modify them.

You can find Senatus here:

https://github.com/PaodingSoftware/senatus-en

Feel free to fork and modify it, and I'd love to hear your feedback in the issues.
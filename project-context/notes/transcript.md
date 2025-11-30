# Thoughts on MCPs: Challenges, Solutions, and a Control Panel Idea

> *Transcribed voice note - 30 November 2025*

---

## Introduction

What I wanted to do in this repository is to record a voice note, which I'm going to be transcribing, setting out really for MCP, why I, and maybe a lot of other users of MCP, both feel like, "Wow, this is really amazing and this is so difficult to use that it's almost—some of us feel like we want to give up on it."

I'll explain the challenges that I'm encountering with MCP use, predominantly Claude Code.

---

## The Core Challenge: Context Overload

The challenge with MCP is one of context at the moment.

Each MCP, and just for disambiguation and clarification, we're talking about the Model Context Protocol for wrapping APIs, each MCP comes with, when you load it into an agent of some kind, it has a tool definition, and each tool definition is lengthy. So, there's a lot of context.

If you are in a project that doesn't require an MCP, and you nevertheless have three or four MCPs universally enabled, what people will find is that the context is being flooded and you're seeing that manifest in:
- Much greater API costs
- Degraded context inference being reached much more quickly

This happens because you've got the system prompt plus the MCP tool definitions consuming your available context window.

---

## Current Solutions Fall Short

The first wave of solutions proposed have been something like: "Well, let's use MCP very, very judiciously. Only use what you need. Disable all the tools you don't need."

The challenge here is that it's not really a very practical way to operate. It's kind of like before you get into a car, saying, "Well, if you don't need the air conditioning now because it's winter, before you get into the car, make sure to rip out the air conditioner," to give a rough analogy.

You spend more time thinking about whether you need this MCP before you even get into a project, which kind of defeats the whole purpose.

---

## The Fragmentation Problem

Another challenge is that right now there's a lot of competition—healthy competition in the marketplace for agentic code generation:
- Google just came out with a new IDE
- Anthropic has the lead arguably
- People are using Qwen and GLM and different models to try to make it more affordable

What this means is that a lot of developers end up repeating the same MCP tool definitions because every different model has:
- A slightly different format, or
- The same format in a different storage location on the file system

Claude insists on `claude.md`, and then Google insists on `agents.md` or Codex. As users are just trying to figure out their stack for MCP, the amount of time that gets wasted by dealing with these inconsistent or not interlinked ways of operating for each vendor becomes a real pain.

---

## Local vs Remote MCPs

There are two different types of MCPs: remote and local.

Some MCPs are useful on the local network. For example, I have:
- A home inventory system
- Home Assistant

It's very useful to be able to access these on the local network. It would be nice to make them remote accessible, but there's a security aspect there that makes me hesitant.

---

## The Value When It Works

I now have a mixture of my own MCPs and well-known ones. For example:
- **Gemini transcription MCP** (my own, on NPM) - Probably one of the most useful aspects of MCP for me is speech to text. I wanted one that would take an audio file, transcribe it, and also do that with a cleanup system prompt. I couldn't find one that did exactly that, so I vibe coded it.
- **Replicate** - For generating images
- **Hugging Face** - For ML workflows

There are a few that really add substantial value. Once you get into them, they're brilliant to have.

### Example Workflow

The potential when you combine them with a large language model is huge. You can say: "Scan the readme. Try to think of a couple of images that could really make this more interesting."

The model then:
1. Does that thinking
2. Turns to Replicate to actually do the text-to-image
3. Pulls those images down into the repository

You might like them, you might hate them, you might have to edit them, but fundamentally, the workflow there is beautiful and much sped up. So when it works, it's got huge potential, which is why I'm a big believer in it.

---

## What I'm Looking For: An MCP Control Panel

What makes the most sense to me is probably something like an **MCP control panel** on your computer. I'm using Linux as my personal operating system.

### Requirements

That control panel has to be **agent agnostic**, because:
- I'm using Claude Code now
- I'm looking at alternatives like OpenCode
- I might in the future start using local agentic models more

If they're all going to be converging on MCP, I don't want anything centralized that's going to be just intercompatible with Claude or Gemini or Codex. That doesn't make any sense.

### Basic Implementation

Probably the most logical implementation:
1. Connect your MCP proxy to your tool
2. In your control panel, add or remove MCPs

But if you only go that far, you're still going to have to spend time juggling MCPs on and off throughout the day depending on the context—which as I said, I don't think is viable.

---

## The Ideal: An Intelligent MCP Orchestrator

What I was thinking of—I don't know if hopefully someone has thought about this—is kind of an **intelligent MCP orchestrator**, which could be an agent that sits inside of the manager.

### How It Would Work

The orchestrator would say: "Okay, Daniel's working on X, where X is—he's using Claude Code in VS Code and I can see he's working on a documentation project, but nothing more than that. So I know from my memories that he likes to use Replicate for creating images to add to the documentation. So I'm going to:
- Turn **on** Replicate MCP
- Turn **off** Hugging Face because I don't see any reason why he would need that in this context"

It's kind of monitoring your context a little bit, acting as a communication layer between your working context and the MCP configuration.

### GUI with Manual Override

If it is a control panel, I think it has to be a **GUI of some kind**, where you can:
- Override the automatic decisions
- See what the configuration is
- Say "Actually, I do need this" and literally turn it on

The advantage would be:
- Connect this once to whatever tool you're working with
- Centralize your MCP management

---

## Team Considerations

I haven't thought yet, because it's not my personal context, of how this would work in a collaborative or team environment. I'm currently exclusively working as a sole contributor for code stuff, even when it is in a team context, so I don't have to really worry about things like shared MCP credentials.

I think a lot of people are probably in the same boat.

---

## Cloud Sync: The Icing on the Cake

I think MCP is so important, I'd be happy to **pay for this as a standalone consumer service**. It would actually make sense to me that was the model rather than something fully open source, because **syncing your MCP configs to the cloud** would be very useful.

### Use Case

Generally I'm very laptop adverse—I usually don't work with it that much. But let's say for argument's sake, I'm going on a business trip and I want to bring my laptop, and I might need to open up VS Code and work on a project.

**Without cloud sync:** I have to spend time digging through my password manager to find the MCP server JSON, import that to VS Code, etc.

**With cloud sync:** I have my configs, I have my server somewhere, download that from the cloud, update my configs on the laptop—boom, I'm good to go.

---

## Summary: What I'm Looking For

I'm basically looking for ideas for projects I can try. I don't want to try out a whole bunch of them and find none of them really work that well.

**Key requirements:**
1. Agent-agnostic MCP management
2. GUI control panel (Linux compatible)
3. Intelligent context-aware orchestration
4. Manual override capability
5. Cloud sync for configs across devices
6. Willing to pay for a quality solution

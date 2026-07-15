# Free Skills

Free Claude Code skills for my YouTube audience.

Each skill lives in its own folder. Grab the one you want, drop it into your Claude Code skills directory, and start using it. That's the whole setup.

## Skills

| Skill | What it does |
| --- | --- |
| [`fable-goal`](./fable-goal) | Turns a rough, spoken-out-loud idea into one exceptional `/goal` prompt you can paste straight into a fresh Fable session. |

More skills get added here over time.

## How to install a skill

A skill is just a folder with a `SKILL.md` inside. To install one:

1. Download the folder for the skill you want (see [Downloading a single folder](#downloading-a-single-folder) below).
2. Move it into your Claude Code skills directory:
   - **Personal (all projects):** `~/.claude/skills/`
   - **Project-only:** `.claude/skills/` inside the project
3. Restart Claude Code (or start a new session).
4. The skill is now live. Invoke it by typing `/` followed by the skill name, for example `/fable-goal`.

Your folder should end up looking like this:

```
~/.claude/skills/
└── fable-goal/
    └── SKILL.md
```

## Downloading a single folder

You don't have to clone the whole repo. A few easy ways to grab just one folder:

**Option A — clone once, copy what you want**

```bash
git clone https://github.com/duncan-buildroom/freeskills.git
cp -r freeskills/fable-goal ~/.claude/skills/
```

**Option B — download the whole repo as a ZIP**

Click the green **Code** button on the [repo page](https://github.com/duncan-buildroom/freeskills), choose **Download ZIP**, unzip it, and copy the folder you want into `~/.claude/skills/`.

## License

Free to use and modify. Made for builders.

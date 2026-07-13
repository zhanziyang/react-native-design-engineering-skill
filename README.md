# React Native Design Engineering

An AI agent skill for designing, implementing, and reviewing polished motion and touch interactions in Expo and React Native.

This skill translates design-engineering judgment into native React Native patterns. It uses Reanimated and React Native Gesture Handler concepts instead of CSS, DOM, Framer Motion, and browser-only APIs.

## What it covers

- Press feedback, entrances, exits, sheets, cards, lists, and loading states
- Gesture-driven drag, swipe, snap, dismiss, and rubber-banding behavior
- Timing, spring, decay, velocity projection, interruption, and cancellation
- Reduced Motion, accessibility actions, and restrained haptic feedback
- Safe Area, keyboard, scrolling, navigation, and nested-gesture ownership
- iOS and Android verification without inventing unobserved device behavior
- Structured animation reviews with priority and verification fields

## Install

```bash
npx skills@latest add zhanziyang/react-native-design-engineering-skill
```

## Usage

```text
Use $react-native-design-engineering to review and improve this Expo swipe-card interaction.
```

```text
Use $react-native-design-engineering to audit the motion and touch feedback in this React Native screen.
```

The skill may also be discovered automatically when a request involves Expo or React Native motion, Reanimated, Gesture Handler, swipe, drag, sheets, cards, haptics, or reduced motion.

## Scope

The implementation guidance targets Expo and React Native on iOS and Android.

It does not generate Web animation implementations or native SwiftUI, UIKit, Jetpack Compose, or Android Views code. For those platforms, use platform-specific guidance.

## Repository structure

```text
skills/
└── react-native-design-engineering/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        ├── motion-patterns.md
        └── review-checklist.md
```

## Credits

Inspired by [Emil Kowalski's Skills for Design Engineers](https://github.com/emilkowalski/skills) and rewritten for Expo and React Native interaction patterns.

## License

MIT

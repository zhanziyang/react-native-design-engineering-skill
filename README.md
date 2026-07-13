# React Native Design Engineering Skills

Five independently triggerable AI agent skills for designing, implementing, naming, reviewing, and improving polished motion and touch interactions in Expo and React Native.

These skills translate design-engineering judgment into native React Native patterns. They use Reanimated, React Native Gesture Handler, and platform/Expo APIs instead of CSS, DOM, Framer Motion, and browser-only APIs.

## Skills

| Skill | Use it for |
| --- | --- |
| [`react-native-design-engineering`](skills/react-native-design-engineering/SKILL.md) | Design, implement, or polish a specific Expo/React Native interaction, component, screen, or motion system. |
| [`review-react-native-animations`](skills/review-react-native-animations/SKILL.md) | Strict evidence-based review of existing animation, gestures, haptics, reduced motion, and interaction quality. |
| [`improve-react-native-animations`](skills/improve-react-native-animations/SKILL.md) | Whole-project motion audit, prioritized findings, and self-contained improvement plans. |
| [`react-native-animation-vocabulary`](skills/react-native-animation-vocabulary/SKILL.md) | Find the canonical term for a mobile animation or gesture effect. |
| [`apple-design-react-native`](skills/apple-design-react-native/SKILL.md) | Apply fluid Apple interaction principles to Expo and React Native without generating SwiftUI/UIKit code. |

## Install

```bash
npx skills@latest add zhanziyang/react-native-design-engineering-skill
```

## Usage

Direct implementation:

```text
Use $react-native-design-engineering to implement an interruptible Expo swipe card with reduced motion.
```

Strict review:

```text
Use $review-react-native-animations to review this modal animation and return prioritized evidence-based findings.
```

Whole-project audit:

```text
Use $improve-react-native-animations to audit motion across this Expo project.
```

Find a term:

```text
Use $react-native-animation-vocabulary to identify the exact term for this gesture effect.
```

Apple-style interaction reasoning:

```text
Use $apple-design-react-native to shape this bottom sheet with direct manipulation, velocity handoff, and fluid interruption.
```

## Scope

The implementation guidance targets Expo and React Native on iOS and Android.

The skills do not answer native implementation requests with Web animation APIs, SwiftUI, UIKit, Jetpack Compose, or Android Views code. Use platform-specific guidance for those surfaces.

## Repository structure

```text
skills/
├── react-native-design-engineering/
├── review-react-native-animations/
├── improve-react-native-animations/
├── react-native-animation-vocabulary/
└── apple-design-react-native/
```

Each folder is an independent skill with its own trigger metadata and instructions.

## Credits

Inspired by [Emil Kowalski's Skills for Design Engineers](https://github.com/emilkowalski/skills) and rewritten for Expo and React Native interaction patterns.

## License

MIT

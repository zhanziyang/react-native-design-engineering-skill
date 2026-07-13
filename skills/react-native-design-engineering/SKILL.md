---
name: react-native-design-engineering
description: Use when designing, implementing, auditing, or polishing motion and touch interaction in Expo or React Native applications, especially with Reanimated, Gesture Handler, swipe, drag, sheets, cards, press feedback, haptics, or reduced motion.
---

# React Native Design Engineering

## Core Principle

Make motion explain state, preserve spatial continuity, or confirm an action. Ask what purpose each effect serves and how often people encounter it; frequent interactions should be immediate and restrained, while intentional play belongs only where it supports the product.

## Workflow

1. Inspect the actual Expo/React Native project, dependency files, installed versions, platform folders, and existing interaction primitives before proposing APIs. Prefer React Native Reanimated and React Native Gesture Handler when they already exist; do not assume their versions.
2. State the intended behavior, gesture ownership, commit conditions, interruption behavior, accessibility equivalent, and platform verification plan.
3. Read [motion-patterns.md](references/motion-patterns.md) for implementation details. Patch the existing stack rather than introducing a parallel animation system without cause.
4. Implement the smallest coherent behavior, including entrances/exits, loading or list transitions, Safe Area, keyboard, navigation, and scroll composition where relevant.
5. Verify on the platforms actually available. Report simulator/device and iOS/Android results separately, and label every unobserved state as unverified.

For strict reviews, read [review-checklist.md](references/review-checklist.md) and require code or runtime evidence before making findings.

## Platform Guardrails

- Target Expo and React Native on iOS and Android. Use native React Native primitives.
- Never answer a native implementation request with CSS, DOM, WAAPI, browser media queries, Framer Motion, or Pointer Events. Isolate React Native Web behavior only when Web is explicitly in scope.
- If a request explicitly asks for SwiftUI, UIKit, Jetpack Compose, or Android Views implementation, stop: state that this skill cannot produce that platform code, offer to switch to appropriate platform-specific guidance, and do not generate code or reinterpret the request as React Native.
- Check iOS and Android behavior rather than asserting parity. Do not claim device, keyboard, haptic, blur/material, navigation, or gesture behavior that was not observed.

## Motion Decisions

- Use timing for bounded state changes with a known duration, spring for settling or retargetable spatial motion, and decay for released momentum. Reserve bounce for momentum or intentional play.
- Require immediate press-down feedback. Keep frequent actions quiet; avoid decorative entrances, repeated bounce, and slow confirmation.
- Prefer transform and opacity for per-frame motion. Deliberate layout transitions are valid when layout change is the meaning of the interaction and performance is verified.
- Keep exits mounted until completion. Retarget interrupted motion from its current presentation value instead of restarting from a stale endpoint.
- Define stable loading behavior and intentional insert, remove, and reorder transitions without destabilizing list virtualization.

## Gesture Decisions

- Track direct manipulation continuously at 1:1 finger movement before any documented resistance or rubber-banding.
- Use activation thresholds and dominant-axis intent where accidental diagonal capture is possible.
- Combine translation and velocity for release decisions; define projection, snap points, dismiss thresholds, and off-screen destinations explicitly.
- Handle begin, update, end, cancellation, and finalization. Stop or retarget in-flight animation from its current value.
- Decide ownership among the gesture, nested scrolling, sheets, navigation back gestures, and parent recognizers. Verify simultaneous, exclusive, or failure relationships rather than leaving conflicts implicit.
- Account for Safe Area, keyboard state, content bounds, orientation, and reachable snap points.

## Accessibility and Feedback

- Provide reduced-motion equivalents that preserve state communication while removing or shortening nonessential travel, parallax, scale, and bounce. Inspect the installed animation-library version before choosing its reduced-motion API.
- Keep touch targets, accessibility roles, state, focus, announcements, and non-gesture alternatives intact.
- Use haptics causally and sparingly: at commit, snap, success, warning, or error moments only. Never emit per-frame haptics or blanket every press with feedback; verify support and suppress unsupported or rapid repeats.

## Output Contracts

For implementation, output in this order:

1. Intended interaction behavior.
2. Stack/dependencies detected.
3. Implementation or patch.
4. Reduced-motion and haptic behavior.
5. Verification performed and unverified platform states.

For review, use exactly this findings table:

| Priority | Current behavior | Recommended change | Why | Verification |
| --- | --- | --- | --- | --- |

Then give a verdict containing overall quality, top risk, and highest-value next action. If evidence is missing, request the relevant code or runtime observation instead of inventing findings.

## References

- Read [motion-patterns.md](references/motion-patterns.md) before implementing press, entrance/exit, sheet, swipe/drag card, list, loading, gesture interruption, velocity, snap, Safe Area, keyboard, or scroll-conflict behavior.
- Read [review-checklist.md](references/review-checklist.md) for strict audits and the evidence, priority, table, and verdict contracts.

## Common Mistakes

- Recommending Web-only APIs for native code.
- Selecting animation APIs before inspecting installed versions.
- Animating to completion without cancellation, finalization, or current-value retargeting.
- Ignoring velocity, gesture ownership, nested scrolling, Safe Area, or keyboard effects.
- Using JS-thread React state updates for per-frame gesture or animation values.
- Adding excessive bounce, blanket haptics, or no reduced-motion equivalent.
- Claiming iOS, Android, simulator, or device behavior without observing it.
- Producing native-platform code that belongs to a different skill.

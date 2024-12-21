# Poker Hand Evaluator

A fast poker hand evaluator using bit manipulation algorithms for efficient hand analysis. This package can be used both as a command-line tool and as a module in Vue 3 or Nuxt 3 applications.

## How It Works

The evaluator uses bit manipulation to efficiently analyze poker hands:

- Each card's rank and suit are converted to bit patterns
- Straight detection uses predefined bit patterns
- Hand evaluation follows standard poker rules
- Returns both hand type and relative ranking

## Installation

```bash
npm install poker-hands
```

## Usage

### As a Vue 3 Module

```javascript
import { formatHand } from "poker-hands";

// In your Vue component
export default {
  data() {
    return {
      hand: ["AS", "KS", "QS", "JS", "TS"],
    };
  },
  computed: {
    handEvaluation() {
      return formatHand(this.hand);
    },
  },
};
```

### As a Nuxt 3 Module

```javascript
// plugins/poker.ts
import { formatHand } from 'poker-hands'

export default defineNuxtPlugin(() => {
  return {
    provide: {
      evaluatePokerHand: (hand) => formatHand(hand)
    }
  }
})

// In your component
<script setup>
const { $evaluatePokerHand } = useNuxtApp()
const result = $evaluatePokerHand(['AS', 'KS', 'QS', 'JS', 'TS'])
</script>
```

### Card Format

Cards should be formatted as strings with:

- Rank: 2-9, T (ten), J, Q, K, A
- Suit: C (clubs), D (diamonds), H (hearts), S (spades)

Example: 'AS' = Ace of Spades

### Return Format

The `formatHand` function returns an object:

```javascript
{
  cards: ['AS', 'KS', 'QS', 'JS', 'TS'],
  hand: 'Straight Flush',
  rank: 9
}
```

### Hand Rankings

```javascript
0: 'Invalid Hand'
1: 'High Card'
2: 'One Pair'
3: 'Two Pair'
4: 'Three of a Kind'
5: 'Straight'
6: 'Flush'
7: 'Full House'
8: 'Four of a Kind'
9: 'Straight Flush'
```

## Command Line Usage

```bash
npm start
```

## Development

```bash
git clone <repository-url>
cd poker-hands
npm install
```

## License

ISC

## References

Main reference: [A Poker hand analyzer in JavaScript using bit math](https://www.codeproject.com/Articles/569271/A-Poker-hand-analyzer-in-JavaScript-using-bit-math)

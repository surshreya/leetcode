## Top K Frequent Words

Given an array of strings `words` and an integer `k`, return the **k most frequent strings.**

Return the answer **sorted by the frequency from highest to lowest**. Sort the words with the same frequency by their **lexicographical order**.

**Example 1**

```bash
Input: words = ["i","love","leetcode","i","love","coding"], k = 2
Output: ["i","love"]
Explanation: "i" and "love" are the two most frequent words.
Note that "i" comes before "love" due to a lower alphabetical order.
```

**Example 2**

```bash
Input: words = ["the","day","is","sunny","the","the","the","sunny","is","is"], k = 4
Output: ["the","is","sunny","day"]
Explanation: "the", "is", "sunny" and "day" are the four most frequent words, with the number of occurrence being 4, 3, 2 and 1 respectively.
```

### Constraints

- `1 <= words.length <= 500`
- `1 <= words[i].length <= 10`
- `words[i] consists of lowercase English letters.`
- `k is in the range [1, The number of unique words[i]]`

## Solution

**_`Sorting`_**

```javascript
/**
 * @param {string[]} words
 * @param {number} k
 * @return {string[]}
 */
var topKFrequent = function (words, k) {
  const freq = new Map();
  words.forEach((word) => {
    freq[word] = (freq[word] || 0) + 1;
  });

  const sorted = Object.entries(freq).sort((a, b) => {
    if (a[1] !== b[1]) {
      return b[1] - a[1];
    } else {
      return a[0].localeCompare(b[0]);
    }
  });
  return sorted.slice(0, k).map((entry) => entry[0]);
};
```

**_`Heap`_**

```javascript
class MinHeap {
  constructor(compareFn) {
    this.compareFn = compareFn;
    this.heap = [];
  }

  size() {
    return this.heap.length;
  }

  push(value) {
    this.heap.push(value);
    this.siftUp(this.heap.length - 1);
  }

  pop() {
    if (this.heap.length === 0) {
      return null;
    }

    const result = this.heap[0];
    const lastElement = this.heap.pop();

    if (this.heap.length > 0) {
      this.heap[0] = lastElement;
      this.siftDown(0);
    }

    return result;
  }

  siftUp(index) {
    let parentIndex = Math.floor((index - 1) / 2);
    while (
      index > 0 &&
      this.compareFn(this.heap[index], this.heap[parentIndex]) < 0
    ) {
      [this.heap[index], this.heap[parentIndex]] = [
        this.heap[parentIndex],
        this.heap[index],
      ];
      index = parentIndex;
      parentIndex = Math.floor((index - 1) / 2);
    }
  }

  siftDown(index) {
    let leftChildIndex = 2 * index + 1;
    let rightChildIndex = 2 * index + 2;
    let minIndex = index;

    if (
      leftChildIndex < this.heap.length &&
      this.compareFn(this.heap[leftChildIndex], this.heap[minIndex]) < 0
    ) {
      minIndex = leftChildIndex;
    }

    if (
      rightChildIndex < this.heap.length &&
      this.compareFn(this.heap[rightChildIndex], this.heap[minIndex]) < 0
    ) {
      minIndex = rightChildIndex;
    }

    if (minIndex !== index) {
      [this.heap[index], this.heap[minIndex]] = [
        this.heap[minIndex],
        this.heap[index],
      ];
      this.siftDown(minIndex);
    }
  }
}

/**
 * @param {string[]} words
 * @param {number} k
 * @return {string[]}
 */
var topKFrequent = function (words, k) {
  const freqMap = new Map();
  for (let word of words) {
    freqMap.set(word, (freqMap.get(word) || 0) + 1);
  }

  const minHeap = new MinHeap((a, b) => {
    if (a.freq !== b.freq) {
      return a.freq - b.freq;
    } else {
      return b.word.localeCompare(a.word);
    }
  });

  for (let [word, freq] of freqMap) {
    minHeap.push({ word, freq });
    if (minHeap.size() > k) {
      minHeap.pop();
    }
  }

  const result = [];
  while (minHeap.size() > 0) {
    result.unshift(minHeap.pop().word);
  }

  return result;
};
```

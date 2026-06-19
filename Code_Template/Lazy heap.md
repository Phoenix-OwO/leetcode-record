

```python
class LazyHeap:
    def __init__(self):
        self.heap = []
        self.remove_cnt = defaultdict(int)  
        self.size = 0 

    def remove(self, x: int) -> None:
        self.remove_cnt[x] += 1 
        self.size -= 1

    def apply_remove(self) -> None:
        while self.heap and self.remove_cnt[self.heap[0]] > 0:
            self.remove_cnt[self.heap[0]] -= 1
            heappop(self.heap)

    def top(self) -> int:
        self.apply_remove()
        return self.heap[0]

    def pop(self) -> int:
        self.apply_remove()
        self.size -= 1
        return heappop(self.heap)

    def push(self, x: int) -> None:
        heappush(self.heap, x)
        self.size += 1

    def pushpop(self, x: int) -> int:
        self.apply_remove()
		return heappushpop(self.heap, x)

```


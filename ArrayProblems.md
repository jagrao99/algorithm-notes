# Real-World Array Problems in Software Engineering

This document covers practical software engineering problems that are efficiently solved using arrays, with Python implementations, complexity analysis, and comparisons to alternative approaches.

## Table of Contents
1. [Image Processing - Pixel Manipulation](#image-processing---pixel-manipulation)
2. [Time Series Data Analysis](#time-series-data-analysis)
3. [Load Balancer - Round Robin Implementation](#load-balancer---round-robin-implementation)
4. [Database Query Result Caching](#database-query-result-caching)
5. [Web Server Request Rate Limiting](#web-server-request-rate-limiting)
6. [Stock Price Moving Average](#stock-price-moving-average)
7. [Memory Pool Management](#memory-pool-management)
8. [Log Aggregation and Analysis](#log-aggregation-and-analysis)
9. [Game Development - Collision Detection](#game-development---collision-detection)
10. [Data Stream Processing](#data-stream-processing)

---

## 1. Image Processing - Pixel Manipulation

### Problem:
Implement image filters (blur, edge detection, brightness adjustment) for a photo editing application.

### Real-World Context:
- Instagram/Snapchat filters
- Medical imaging software
- Computer vision preprocessing
- Photo editing applications

### Array-Based Solution:

```python
import numpy as np
from typing import List, Tuple

class ImageProcessor:
    """
    Real-time image processing using 2D arrays for pixel manipulation.
    Used in applications like Instagram filters, medical imaging, etc.
    """
    
    def __init__(self, width: int, height: int):
        self.width = width
        self.height = height
        
    def apply_gaussian_blur(self, image: List[List[int]], kernel_size: int = 3) -> List[List[int]]:
        """
        Apply Gaussian blur filter using convolution with 2D arrays.
        
        Time Complexity: O(n*m*k²) where n,m are image dimensions, k is kernel size
        Space Complexity: O(n*m) for result image
        """
        # Gaussian kernel for blur effect
        if kernel_size == 3:
            kernel = [
                [1, 2, 1],
                [2, 4, 2],
                [1, 2, 1]
            ]
            kernel_sum = 16
        else:
            # Generate larger kernels dynamically
            kernel = self._generate_gaussian_kernel(kernel_size)
            kernel_sum = sum(sum(row) for row in kernel)
        
        result = [[0 for _ in range(self.width)] for _ in range(self.height)]
        offset = kernel_size // 2
        
        for y in range(offset, self.height - offset):
            for x in range(offset, self.width - offset):
                pixel_sum = 0
                
                # Apply convolution
                for ky in range(kernel_size):
                    for kx in range(kernel_size):
                        pixel_sum += image[y + ky - offset][x + kx - offset] * kernel[ky][kx]
                
                result[y][x] = pixel_sum // kernel_sum
                
        return result
    
    def adjust_brightness(self, image: List[List[int]], factor: float) -> List[List[int]]:
        """
        Adjust image brightness using array element-wise operations.
        
        Time Complexity: O(n*m) - single pass through all pixels
        Space Complexity: O(n*m) for result image
        """
        result = []
        for row in image:
            new_row = []
            for pixel in row:
                # Clamp values between 0-255
                new_pixel = min(255, max(0, int(pixel * factor)))
                new_row.append(new_pixel)
            result.append(new_row)
        
        return result
    
    def detect_edges_sobel(self, image: List[List[int]]) -> List[List[int]]:
        """
        Edge detection using Sobel operator with 2D convolution.
        
        Time Complexity: O(n*m) - optimized single pass
        Space Complexity: O(n*m) for gradient arrays
        """
        # Sobel kernels for edge detection
        sobel_x = [[-1, 0, 1], [-2, 0, 2], [-1, 0, 1]]
        sobel_y = [[-1, -2, -1], [0, 0, 0], [1, 2, 1]]
        
        grad_x = self._apply_kernel(image, sobel_x)
        grad_y = self._apply_kernel(image, sobel_y)
        
        # Combine gradients
        result = [[0 for _ in range(self.width)] for _ in range(self.height)]
        for y in range(self.height):
            for x in range(self.width):
                magnitude = int((grad_x[y][x]**2 + grad_y[y][x]**2)**0.5)
                result[y][x] = min(255, magnitude)
        
        return result
    
    def _apply_kernel(self, image: List[List[int]], kernel: List[List[int]]) -> List[List[int]]:
        """Helper method for kernel convolution."""
        result = [[0 for _ in range(self.width)] for _ in range(self.height)]
        
        for y in range(1, self.height - 1):
            for x in range(1, self.width - 1):
                pixel_sum = 0
                for ky in range(3):
                    for kx in range(3):
                        pixel_sum += image[y + ky - 1][x + kx - 1] * kernel[ky][kx]
                result[y][x] = pixel_sum
        
        return result

# Example usage
def demo_image_processing():
    # Sample 8x8 grayscale image
    sample_image = [
        [100, 120, 140, 160, 180, 200, 220, 240],
        [110, 130, 150, 170, 190, 210, 230, 250],
        [120, 140, 160, 180, 200, 220, 240, 255],
        [130, 150, 170, 190, 210, 230, 250, 255],
        [140, 160, 180, 200, 220, 240, 255, 255],
        [150, 170, 190, 210, 230, 250, 255, 255],
        [160, 180, 200, 220, 240, 255, 255, 255],
        [170, 190, 210, 230, 250, 255, 255, 255]
    ]
    
    processor = ImageProcessor(8, 8)
    
    # Apply filters
    blurred = processor.apply_gaussian_blur(sample_image)
    brightened = processor.adjust_brightness(sample_image, 1.2)
    edges = processor.detect_edges_sobel(sample_image)
    
    print("Original vs Processed images ready for display")
```

### Why This Approach is Best:

**Advantages over alternatives:**
1. **Memory Efficiency**: 2D arrays provide contiguous memory layout for cache-friendly access
2. **Vectorization**: Can leverage SIMD instructions for parallel pixel processing
3. **GPU Acceleration**: Easy to port to GPU kernels for massive parallelization

**Alternative Approaches:**
- **Object-oriented pixels**: Much slower due to object overhead
- **Functional approach**: Higher memory usage due to immutability
- **Database storage**: Too slow for real-time processing

---

## 2. Time Series Data Analysis

### Problem:
Analyze real-time sensor data for anomaly detection in IoT systems.

### Real-World Context:
- Server monitoring (CPU, memory, network)
- Financial trading systems
- Industrial sensor networks
- Health monitoring devices

### Array-Based Solution:

```python
from collections import deque
import statistics
from typing import List, Optional, Tuple

class TimeSeriesAnalyzer:
    """
    Real-time time series analysis using circular buffers and sliding windows.
    Used in monitoring systems, trading platforms, IoT sensor networks.
    """
    
    def __init__(self, window_size: int = 100):
        self.window_size = window_size
        self.data_buffer = deque(maxlen=window_size)  # Circular buffer
        self.timestamps = deque(maxlen=window_size)
        self.anomaly_threshold = 2.0  # Standard deviations
        
    def add_data_point(self, value: float, timestamp: float) -> Optional[dict]:
        """
        Add new data point and detect anomalies in O(1) amortized time.
        
        Time Complexity: O(1) amortized for addition, O(k) for analysis where k=window_size
        Space Complexity: O(k) for fixed-size circular buffer
        """
        self.data_buffer.append(value)
        self.timestamps.append(timestamp)
        
        if len(self.data_buffer) >= self.window_size:
            return self._analyze_current_window()
        return None
    
    def _analyze_current_window(self) -> dict:
        """
        Analyze current window for anomalies and trends.
        
        Uses statistical methods optimized for array operations.
        """
        data_array = list(self.data_buffer)
        
        # Calculate statistics efficiently
        mean_val = statistics.mean(data_array)
        stdev_val = statistics.stdev(data_array) if len(data_array) > 1 else 0
        
        current_value = data_array[-1]
        z_score = (current_value - mean_val) / stdev_val if stdev_val > 0 else 0
        
        # Trend analysis using linear regression on array
        trend = self._calculate_trend(data_array)
        
        # Detect anomalies
        is_anomaly = abs(z_score) > self.anomaly_threshold
        
        return {
            'current_value': current_value,
            'mean': mean_val,
            'std_dev': stdev_val,
            'z_score': z_score,
            'trend': trend,
            'is_anomaly': is_anomaly,
            'window_size': len(data_array)
        }
    
    def _calculate_trend(self, data: List[float]) -> str:
        """
        Calculate trend using simple linear regression on array.
        
        Time Complexity: O(n) where n is window size
        Space Complexity: O(1) - only stores slope
        """
        n = len(data)
        if n < 2:
            return "insufficient_data"
        
        # Linear regression: y = mx + b
        x_values = list(range(n))
        x_mean = (n - 1) / 2
        y_mean = sum(data) / n
        
        # Calculate slope efficiently
        numerator = sum((x - x_mean) * (y - y_mean) for x, y in zip(x_values, data))
        denominator = sum((x - x_mean) ** 2 for x in x_values)
        
        if denominator == 0:
            return "flat"
        
        slope = numerator / denominator
        
        if slope > 0.1:
            return "increasing"
        elif slope < -0.1:
            return "decreasing"
        else:
            return "stable"
    
    def get_moving_average(self, period: int) -> List[float]:
        """
        Calculate moving average using sliding window technique.
        
        Time Complexity: O(n) where n is data buffer size
        Space Complexity: O(n-period+1) for result array
        """
        if len(self.data_buffer) < period:
            return []
        
        data_list = list(self.data_buffer)
        moving_averages = []
        
        # Use sliding window for efficient calculation
        window_sum = sum(data_list[:period])
        moving_averages.append(window_sum / period)
        
        # Slide the window
        for i in range(period, len(data_list)):
            window_sum = window_sum - data_list[i - period] + data_list[i]
            moving_averages.append(window_sum / period)
        
        return moving_averages

# Real-world example: Server CPU monitoring
def demo_server_monitoring():
    analyzer = TimeSeriesAnalyzer(window_size=50)
    
    # Simulate CPU usage data
    import random
    import time
    
    base_cpu = 25.0  # Normal CPU usage
    
    for i in range(100):
        # Simulate normal operation with occasional spikes
        if i % 20 == 0:  # Simulate CPU spike every 20 readings
            cpu_usage = base_cpu + random.uniform(40, 60)  # Spike
        else:
            cpu_usage = base_cpu + random.uniform(-5, 15)  # Normal variation
        
        timestamp = time.time() + i
        result = analyzer.add_data_point(cpu_usage, timestamp)
        
        if result and result['is_anomaly']:
            print(f"ALERT: CPU anomaly detected at {timestamp}")
            print(f"Current: {result['current_value']:.2f}%, Z-score: {result['z_score']:.2f}")
            print(f"Trend: {result['trend']}")
```

### Why This Approach is Best:

**Advantages:**
1. **O(1) Insertion**: Circular buffer provides constant-time data addition
2. **Memory Efficient**: Fixed-size buffer prevents memory leaks
3. **Cache Friendly**: Array access patterns optimize CPU cache usage
4. **Real-time Processing**: Can handle high-frequency data streams

**Alternative Approaches:**
- **Database storage**: Too slow for real-time analysis
- **Linked lists**: Poor cache performance, no random access
- **Full history storage**: Memory grows unbounded

---

## 3. Load Balancer - Round Robin Implementation

### Problem:
Implement a load balancer that distributes requests across multiple servers using round-robin algorithm.

### Real-World Context:
- Web application load balancing
- Microservices traffic distribution
- Database connection pooling
- CDN request routing

### Array-Based Solution:

```python
from typing import List, Optional
import time
import threading
from dataclasses import dataclass

@dataclass
class Server:
    """Represents a backend server."""
    id: str
    host: str
    port: int
    is_healthy: bool = True
    request_count: int = 0
    last_health_check: float = 0

class LoadBalancer:
    """
    Round-robin load balancer using array for O(1) server selection.
    Used in production systems like NGINX, HAProxy, AWS ALB.
    """
    
    def __init__(self, servers: List[Server]):
        self.servers = servers.copy()  # Array of servers
        self.current_index = 0  # Round-robin pointer
        self.total_requests = 0
        self.lock = threading.Lock()  # Thread safety
        
    def get_next_server(self) -> Optional[Server]:
        """
        Get next available server using round-robin algorithm.
        
        Time Complexity: O(n) worst case (all servers unhealthy), O(1) average case
        Space Complexity: O(1) - only stores index pointer
        """
        if not self.servers:
            return None
        
        with self.lock:  # Thread-safe operation
            start_index = self.current_index
            attempts = 0
            
            while attempts < len(self.servers):
                server = self.servers[self.current_index]
                
                # Move to next server for next request
                self.current_index = (self.current_index + 1) % len(self.servers)
                
                if server.is_healthy:
                    server.request_count += 1
                    self.total_requests += 1
                    return server
                
                attempts += 1
            
            # No healthy servers available
            return None
    
    def add_server(self, server: Server) -> None:
        """
        Add new server to the pool.
        
        Time Complexity: O(1) - array append
        Space Complexity: O(1)
        """
        with self.lock:
            self.servers.append(server)
    
    def remove_server(self, server_id: str) -> bool:
        """
        Remove server from the pool.
        
        Time Complexity: O(n) - array search and removal
        Space Complexity: O(1)
        """
        with self.lock:
            for i, server in enumerate(self.servers):
                if server.id == server_id:
                    # Adjust current index if necessary
                    if i < self.current_index:
                        self.current_index -= 1
                    elif i == self.current_index and self.current_index >= len(self.servers) - 1:
                        self.current_index = 0
                    
                    self.servers.pop(i)
                    return True
            return False
    
    def mark_server_unhealthy(self, server_id: str) -> None:
        """
        Mark server as unhealthy (health check failure).
        
        Time Complexity: O(n) - linear search
        Space Complexity: O(1)
        """
        with self.lock:
            for server in self.servers:
                if server.id == server_id:
                    server.is_healthy = False
                    break
    
    def get_server_stats(self) -> dict:
        """
        Get load balancing statistics.
        
        Time Complexity: O(n) - iterate through servers
        Space Complexity: O(n) - create stats dictionary
        """
        with self.lock:
            healthy_servers = sum(1 for s in self.servers if s.is_healthy)
            total_servers = len(self.servers)
            
            server_loads = [
                {
                    'id': s.id,
                    'host': s.host,
                    'requests': s.request_count,
                    'healthy': s.is_healthy,
                    'load_percentage': (s.request_count / self.total_requests * 100) 
                                     if self.total_requests > 0 else 0
                }
                for s in self.servers
            ]
            
            return {
                'total_requests': self.total_requests,
                'healthy_servers': healthy_servers,
                'total_servers': total_servers,
                'current_index': self.current_index,
                'server_details': server_loads
            }

class HealthChecker:
    """Health checker for monitoring server availability."""
    
    def __init__(self, load_balancer: LoadBalancer, check_interval: int = 30):
        self.load_balancer = load_balancer
        self.check_interval = check_interval
        self.running = False
    
    def start_health_checks(self):
        """Start background health checking."""
        self.running = True
        threading.Thread(target=self._health_check_loop, daemon=True).start()
    
    def _health_check_loop(self):
        """Simulate health checking (would use actual HTTP requests in production)."""
        while self.running:
            current_time = time.time()
            
            for server in self.load_balancer.servers:
                # Simulate health check (replace with actual HTTP ping)
                if current_time - server.last_health_check > self.check_interval:
                    server.is_healthy = self._ping_server(server)
                    server.last_health_check = current_time
            
            time.sleep(self.check_interval)
    
    def _ping_server(self, server: Server) -> bool:
        """Simulate server health check."""
        import random
        # In real implementation, would make HTTP request to server
        # Simulate 95% uptime
        return random.random() > 0.05

# Example usage
def demo_load_balancer():
    # Create servers
    servers = [
        Server("web1", "192.168.1.10", 8080),
        Server("web2", "192.168.1.11", 8080),
        Server("web3", "192.168.1.12", 8080),
    ]
    
    # Initialize load balancer
    lb = LoadBalancer(servers)
    
    # Start health checking
    health_checker = HealthChecker(lb)
    health_checker.start_health_checks()
    
    # Simulate incoming requests
    print("Simulating 20 requests:")
    for i in range(20):
        server = lb.get_next_server()
        if server:
            print(f"Request {i+1} -> Server {server.id} ({server.host}:{server.port})")
        else:
            print(f"Request {i+1} -> No healthy servers available!")
    
    # Print statistics
    stats = lb.get_server_stats()
    print(f"\nLoad Balancer Stats:")
    print(f"Total Requests: {stats['total_requests']}")
    print(f"Healthy Servers: {stats['healthy_servers']}/{stats['total_servers']}")
    
    for server_stat in stats['server_details']:
        print(f"Server {server_stat['id']}: {server_stat['requests']} requests "
              f"({server_stat['load_percentage']:.1f}%)")
```

### Why This Approach is Best:

**Advantages:**
1. **O(1) Average Case**: Array indexing provides constant-time server selection
2. **Memory Efficient**: Stores only server references, not request history
3. **Thread Safe**: Atomic operations on array index
4. **Predictable Performance**: No hash collisions or tree rebalancing

**Alternative Approaches:**
- **Weighted round-robin**: More complex but handles different server capacities
- **Least connections**: Requires tracking active connections per server
- **Hash-based**: Can cause uneven distribution with server failures

---

## 4. Database Query Result Caching

### Problem:
Implement an LRU (Least Recently Used) cache for database query results to improve application performance.

### Real-World Context:
- Web application response caching
- Database query optimization
- API response caching
- Content delivery networks

### Array-Based Solution:

```python
from typing import Any, Optional, Dict
import time
from dataclasses import dataclass

@dataclass
class CacheEntry:
    """Represents a cached query result."""
    key: str
    value: Any
    timestamp: float
    access_count: int = 0
    size_bytes: int = 0

class LRUCache:
    """
    LRU Cache implementation using array + hash table for O(1) operations.
    Used in Redis, Memcached, application-level caching.
    """
    
    def __init__(self, capacity: int, ttl_seconds: int = 3600):
        self.capacity = capacity
        self.ttl_seconds = ttl_seconds
        
        # Array-based storage for cache entries
        self.cache_array: List[Optional[CacheEntry]] = [None] * capacity
        self.key_to_index: Dict[str, int] = {}  # Hash table for O(1) lookup
        
        # LRU tracking using array indices
        self.access_order: List[int] = []  # Most recent at end
        self.free_slots: List[int] = list(range(capacity))  # Available indices
        
        # Statistics
        self.hits = 0
        self.misses = 0
        self.evictions = 0
    
    def get(self, key: str) -> Optional[Any]:
        """
        Retrieve value from cache.
        
        Time Complexity: O(1) average case for hash lookup + O(k) for LRU update
        Space Complexity: O(1)
        """
        if key not in self.key_to_index:
            self.misses += 1
            return None
        
        index = self.key_to_index[key]
        entry = self.cache_array[index]
        
        # Check if entry has expired
        if entry and self._is_expired(entry):
            self._remove_entry(key, index)
            self.misses += 1
            return None
        
        if entry:
            # Update access statistics
            entry.access_count += 1
            self._update_access_order(index)
            self.hits += 1
            return entry.value
        
        self.misses += 1
        return None
    
    def put(self, key: str, value: Any, size_bytes: int = 0) -> bool:
        """
        Store value in cache with LRU eviction.
        
        Time Complexity: O(1) for insertion + O(k) for LRU update
        Space Complexity: O(1)
        """
        current_time = time.time()
        
        # Update existing entry
        if key in self.key_to_index:
            index = self.key_to_index[key]
            entry = self.cache_array[index]
            if entry:
                entry.value = value
                entry.timestamp = current_time
                entry.size_bytes = size_bytes
                self._update_access_order(index)
                return True
        
        # Need new slot
        if self.free_slots:
            # Use free slot
            index = self.free_slots.pop()
        else:
            # Evict LRU entry
            index = self._evict_lru()
            if index == -1:
                return False  # Cache full, couldn't evict
        
        # Create new entry
        new_entry = CacheEntry(
            key=key,
            value=value,
            timestamp=current_time,
            size_bytes=size_bytes
        )
        
        self.cache_array[index] = new_entry
        self.key_to_index[key] = index
        self._update_access_order(index)
        
        return True
    
    def _evict_lru(self) -> int:
        """
        Evict least recently used entry.
        
        Time Complexity: O(1) - access first element of access_order array
        Space Complexity: O(1)
        """
        if not self.access_order:
            return -1
        
        # LRU is at the beginning of access_order array
        lru_index = self.access_order.pop(0)
        entry = self.cache_array[lru_index]
        
        if entry:
            # Remove from hash table
            del self.key_to_index[entry.key]
            # Clear array slot
            self.cache_array[lru_index] = None
            self.evictions += 1
        
        return lru_index
    
    def _update_access_order(self, index: int) -> None:
        """
        Update LRU access order.
        
        Time Complexity: O(k) where k is number of entries (for list operations)
        Space Complexity: O(1)
        """
        # Remove from current position
        if index in self.access_order:
            self.access_order.remove(index)
        
        # Add to end (most recently used)
        self.access_order.append(index)
    
    def _is_expired(self, entry: CacheEntry) -> bool:
        """Check if cache entry has expired."""
        return (time.time() - entry.timestamp) > self.ttl_seconds
    
    def _remove_entry(self, key: str, index: int) -> None:
        """Remove expired entry from cache."""
        if key in self.key_to_index:
            del self.key_to_index[key]
        
        self.cache_array[index] = None
        
        if index in self.access_order:
            self.access_order.remove(index)
        
        self.free_slots.append(index)
    
    def get_cache_stats(self) -> Dict[str, Any]:
        """
        Get cache performance statistics.
        
        Time Complexity: O(n) to calculate size and memory usage
        Space Complexity: O(1)
        """
        total_entries = sum(1 for entry in self.cache_array if entry is not None)
        total_memory = sum(entry.size_bytes for entry in self.cache_array if entry is not None)
        
        hit_rate = self.hits / (self.hits + self.misses) if (self.hits + self.misses) > 0 else 0
        
        return {
            'capacity': self.capacity,
            'current_size': total_entries,
            'memory_usage_bytes': total_memory,
            'hits': self.hits,
            'misses': self.misses,
            'evictions': self.evictions,
            'hit_rate': hit_rate,
            'free_slots': len(self.free_slots)
        }

class DatabaseQueryCache:
    """High-level database query cache using LRU cache."""
    
    def __init__(self, capacity: int = 1000, ttl_seconds: int = 3600):
        self.cache = LRUCache(capacity, ttl_seconds)
    
    def get_query_result(self, query: str, params: tuple = ()) -> Optional[Any]:
        """
        Get cached query result.
        
        Time Complexity: O(1) average case
        Space Complexity: O(1)
        """
        cache_key = self._generate_cache_key(query, params)
        return self.cache.get(cache_key)
    
    def cache_query_result(self, query: str, params: tuple, result: Any) -> bool:
        """
        Cache query result.
        
        Time Complexity: O(1) average case
        Space Complexity: O(1)
        """
        cache_key = self._generate_cache_key(query, params)
        
        # Estimate result size (simplified)
        size_bytes = len(str(result)) * 2  # Rough estimate
        
        return self.cache.put(cache_key, result, size_bytes)
    
    def _generate_cache_key(self, query: str, params: tuple) -> str:
        """Generate unique cache key for query + parameters."""
        import hashlib
        
        # Create deterministic key from query and parameters
        query_hash = hashlib.md5(query.encode()).hexdigest()
        params_hash = hashlib.md5(str(params).encode()).hexdigest()
        
        return f"{query_hash}:{params_hash}"

# Example usage
def demo_query_cache():
    # Initialize cache
    query_cache = DatabaseQueryCache(capacity=100, ttl_seconds=300)
    
    # Simulate database queries
    queries = [
        ("SELECT * FROM users WHERE age > ?", (25,)),
        ("SELECT COUNT(*) FROM orders WHERE date = ?", ("2024-01-01",)),
        ("SELECT * FROM products WHERE category = ?", ("electronics",)),
        ("SELECT * FROM users WHERE age > ?", (25,)),  # Duplicate - should hit cache
    ]
    
    # Simulate query results
    mock_results = [
        [{"id": 1, "name": "John", "age": 30}, {"id": 2, "name": "Jane", "age": 28}],
        [{"count": 150}],
        [{"id": 1, "name": "Laptop", "price": 999.99}],
        None  # This will be served from cache
    ]
    
    print("Database Query Cache Demo:")
    
    for i, (query, params) in enumerate(queries):
        # Try to get from cache first
        cached_result = query_cache.get_query_result(query, params)
        
        if cached_result is not None:
            print(f"Query {i+1}: Cache HIT")
            print(f"Result: {cached_result}")
        else:
            print(f"Query {i+1}: Cache MISS - executing query")
            # Simulate database execution
            result = mock_results[i] if i < len(mock_results) else []
            
            # Cache the result
            query_cache.cache_query_result(query, params, result)
            print(f"Result: {result}")
        
        print()
    
    # Print cache statistics
    stats = query_cache.cache.get_cache_stats()
    print("Cache Statistics:")
    for key, value in stats.items():
        print(f"{key}: {value}")
```

### Why This Approach is Best:

**Advantages:**
1. **O(1) Operations**: Array indexing + hash table provides constant-time access
2. **Memory Efficient**: Fixed-size array prevents unbounded growth
3. **Cache-Friendly**: Array layout improves CPU cache performance
4. **Predictable Performance**: No dynamic allocation during normal operations

**Alternative Approaches:**
- **Linked List LRU**: O(n) for updates, poor cache locality
- **Tree-based LRU**: O(log n) operations, more complex
- **Simple hash table**: No eviction policy, memory grows unbounded

---

## 5. Web Server Request Rate Limiting

### Problem:
Implement rate limiting to prevent API abuse and ensure fair resource usage.

### Real-World Context:
- API rate limiting (Twitter, GitHub APIs)
- DDoS protection
- Fair usage enforcement
- Resource quota management

### Array-Based Solution:

```python
import time
import threading
from typing import Dict, List, Optional
from dataclasses import dataclass
from enum import Enum

class RateLimitResult(Enum):
    ALLOWED = "allowed"
    RATE_LIMITED = "rate_limited"
    QUOTA_EXCEEDED = "quota_exceeded"

@dataclass
class RateLimitConfig:
    """Configuration for rate limiting."""
    requests_per_second: int
    requests_per_minute: int
    requests_per_hour: int
    burst_capacity: int

class TokenBucketRateLimiter:
    """
    Token bucket rate limiter using array for efficient token management.
    Used in API gateways, web servers, cloud services.
    """
    
    def __init__(self, config: RateLimitConfig):
        self.config = config
        
        # Token buckets for different time windows (array-based)
        self.tokens_per_second = config.requests_per_second
        self.tokens_per_minute = config.requests_per_minute
        self.tokens_per_hour = config.requests_per_hour
        
        # Current token counts
        self.current_tokens_second = config.requests_per_second
        self.current_tokens_minute = config.requests_per_minute
        self.current_tokens_hour = config.requests_per_hour
        
        # Time tracking
        self.last_refill_time = time.time()
        self.lock = threading.Lock()
        
        # Request tracking arrays (circular buffers)
        self.second_requests = [0] * 60  # Track requests per second over last minute
        self.minute_requests = [0] * 60  # Track requests per minute over last hour
        self.current_second_index = 0
        self.current_minute_index = 0
        
    def is_request_allowed(self, client_id: str, tokens_requested: int = 1) -> tuple[RateLimitResult, dict]:
        """
        Check if request is allowed based on rate limits.
        
        Time Complexity: O(1) - constant time token bucket operations
        Space Complexity: O(1) - fixed size arrays
        """
        with self.lock:
            current_time = time.time()
            
            # Refill tokens based on elapsed time
            self._refill_tokens(current_time)
            
            # Update request tracking arrays
            self._update_request_tracking(current_time)
            
            # Check all rate limits
            if self.current_tokens_second < tokens_requested:
                return RateLimitResult.RATE_LIMITED, self._get_rate_limit_info("per_second")
            
            if self.current_tokens_minute < tokens_requested:
                return RateLimitResult.RATE_LIMITED, self._get_rate_limit_info("per_minute")
            
            if self.current_tokens_hour < tokens_requested:
                return RateLimitResult.RATE_LIMITED, self._get_rate_limit_info("per_hour")
            
            # Consume tokens
            self.current_tokens_second -= tokens_requested
            self.current_tokens_minute -= tokens_requested
            self.current_tokens_hour -= tokens_requested
            
            # Record request in tracking arrays
            self.second_requests[self.current_second_index] += tokens_requested
            self.minute_requests[self.current_minute_index] += tokens_requested
            
            return RateLimitResult.ALLOWED, self._get_rate_limit_info("allowed")
    
    def _refill_tokens(self, current_time: float) -> None:
        """
        Refill token buckets based on elapsed time.
        
        Time Complexity: O(1) - mathematical calculation
        Space Complexity: O(1)
        """
        elapsed = current_time - self.last_refill_time
        
        if elapsed >= 1.0:  # Refill every second
            # Refill per-second bucket
            self.current_tokens_second = min(
                self.tokens_per_second,
                self.current_tokens_second + int(elapsed) * self.tokens_per_second
            )
            
            # Refill per-minute bucket
            self.current_tokens_minute = min(
                self.tokens_per_minute,
                self.current_tokens_minute + int(elapsed * self.tokens_per_minute / 60)
            )
            
            # Refill per-hour bucket
            self.current_tokens_hour = min(
                self.tokens_per_hour,
                self.current_tokens_hour + int(elapsed * self.tokens_per_hour / 3600)
            )
            
            self.last_refill_time = current_time
    
    def _update_request_tracking(self, current_time: float) -> None:
        """
        Update circular arrays for request tracking.
        
        Time Complexity: O(1) - array index updates
        Space Complexity: O(1)
        """
        current_second = int(current_time) % 60
        current_minute = int(current_time // 60) % 60
        
        # Reset arrays if we've moved to a new time slot
        if current_second != self.current_second_index:
            self.second_requests[current_second] = 0
            self.current_second_index = current_second
        
        if current_minute != self.current_minute_index:
            self.minute_requests[current_minute] = 0
            self.current_minute_index = current_minute
    
    def _get_rate_limit_info(self, limit_type: str) -> dict:
        """Get current rate limit status information."""
        return {
            'limit_type': limit_type,
            'tokens_remaining_second': self.current_tokens_second,
            'tokens_remaining_minute': self.current_tokens_minute,
            'tokens_remaining_hour': self.current_tokens_hour,
            'reset_time_second': self.last_refill_time + 1,
            'reset_time_minute': self.last_refill_time + 60,
            'reset_time_hour': self.last_refill_time + 3600,
        }

class AdvancedRateLimiter:
    """
    Advanced rate limiter with per-client tracking using arrays.
    """
    
    def __init__(self, default_config: RateLimitConfig, max_clients: int = 10000):
        self.default_config = default_config
        self.max_clients = max_clients
        
        # Client rate limiters stored in hash table with array-based limiters
        self.client_limiters: Dict[str, TokenBucketRateLimiter] = {}
        self.client_access_times: Dict[str, float] = {}
        
        # Array for tracking global request patterns
        self.global_request_history = [0] * 3600  # Requests per second over last hour
        self.global_history_index = 0
        self.last_global_update = time.time()
        
        self.lock = threading.Lock()
    
    def check_request(self, client_id: str, request_size: int = 1) -> tuple[RateLimitResult, dict]:
        """
        Check if request from specific client is allowed.
        
        Time Complexity: O(1) average case (hash lookup + token bucket operations)
        Space Complexity: O(k) where k is number of active clients
        """
        with self.lock:
            current_time = time.time()
            
            # Update global tracking
            self._update_global_tracking(current_time)
            
            # Get or create rate limiter for this client
            if client_id not in self.client_limiters:
                if len(self.client_limiters) >= self.max_clients:
                    # Evict oldest client
                    self._evict_oldest_client()
                
                self.client_limiters[client_id] = TokenBucketRateLimiter(self.default_config)
            
            # Update client access time
            self.client_access_times[client_id] = current_time
            
            # Check rate limit for this client
            result, info = self.client_limiters[client_id].is_request_allowed(client_id, request_size)
            
            # Update global statistics
            if result == RateLimitResult.ALLOWED:
                self.global_request_history[self.global_history_index] += request_size
            
            # Add global information
            info['global_requests_per_second'] = self._calculate_global_rps()
            info['active_clients'] = len(self.client_limiters)
            
            return result, info
    
    def _update_global_tracking(self, current_time: float) -> None:
        """
        Update global request tracking array.
        
        Time Complexity: O(1) - array operations
        Space Complexity: O(1)
        """
        elapsed = current_time - self.last_global_update
        
        if elapsed >= 1.0:
            # Move to next second in circular array
            seconds_elapsed = int(elapsed)
            for _ in range(min(seconds_elapsed, 3600)):
                self.global_history_index = (self.global_history_index + 1) % 3600
                self.global_request_history[self.global_history_index] = 0
            
            self.last_global_update = current_time
    
    def _evict_oldest_client(self) -> None:
        """
        Evict least recently used client.
        
        Time Complexity: O(n) where n is number of clients
        Space Complexity: O(1)
        """
        if not self.client_access_times:
            return
        
        # Find client with oldest access time
        oldest_client = min(self.client_access_times.items(), key=lambda x: x[1])[0]
        
        # Remove from both dictionaries
        del self.client_limiters[oldest_client]
        del self.client_access_times[oldest_client]
    
    def _calculate_global_rps(self) -> float:
        """
        Calculate global requests per second using circular array.
        
        Time Complexity: O(k) where k is window size (60 seconds)
        Space Complexity: O(1)
        """
        # Sum requests in last 60 seconds
        total_requests = 0
        for i in range(60):
            index = (self.global_history_index - i) % 3600
            total_requests += self.global_request_history[index]
        
        return total_requests / 60.0
    
    def get_system_stats(self) -> dict:
        """
        Get comprehensive system statistics.
        
        Time Complexity: O(n) where n is number of clients
        Space Complexity: O(n) for statistics dictionary
        """
        with self.lock:
            current_time = time.time()
            
            # Calculate statistics
            active_clients = len(self.client_limiters)
            global_rps = self._calculate_global_rps()
            
            # Find busiest clients
            client_stats = []
            for client_id, limiter in self.client_limiters.items():
                client_stats.append({
                    'client_id': client_id,
                    'last_access': self.client_access_times.get(client_id, 0),
                    'tokens_remaining': limiter.current_tokens_second
                })
            
            # Sort by last access time
            client_stats.sort(key=lambda x: x['last_access'], reverse=True)
            
            return {
                'active_clients': active_clients,
                'global_requests_per_second': global_rps,
                'top_clients': client_stats[:10],  # Top 10 most active
                'total_capacity': self.max_clients,
                'memory_usage_estimate': active_clients * 1024,  # Rough estimate
            }

# Example usage
def demo_rate_limiting():
    # Configure rate limits
    config = RateLimitConfig(
        requests_per_second=10,
        requests_per_minute=100,
        requests_per_hour=1000,
        burst_capacity=20
    )
    
    # Initialize rate limiter
    rate_limiter = AdvancedRateLimiter(config, max_clients=1000)
    
    print("Rate Limiting Demo:")
    
    # Simulate requests from multiple clients
    clients = ["user1", "user2", "user3"]
    
    for i in range(50):
        client_id = clients[i % len(clients)]
        
        # Make request
        result, info = rate_limiter.check_request(client_id)
        
        if result == RateLimitResult.ALLOWED:
            print(f"Request {i+1} from {client_id}: ALLOWED")
        else:
            print(f"Request {i+1} from {client_id}: {result.value}")
            print(f"  Tokens remaining: {info['tokens_remaining_second']}")
        
        # Small delay to simulate real requests
        time.sleep(0.1)
        
        # Print stats every 10 requests
        if (i + 1) % 10 == 0:
            stats = rate_limiter.get_system_stats()
            print(f"\nSystem Stats after {i+1} requests:")
            print(f"Active clients: {stats['active_clients']}")
            print(f"Global RPS: {stats['global_requests_per_second']:.2f}")
            print()
```

### Why This Approach is Best:

**Advantages:**
1. **O(1) Request Processing**: Token bucket with array-based tracking
2. **Memory Efficient**: Fixed-size circular arrays prevent memory growth
3. **Thread Safe**: Atomic operations on array indices
4. **Scalable**: Can handle thousands of concurrent clients

**Alternative Approaches:**
- **Sliding window**: More accurate but O(n) complexity
- **Fixed window**: Can allow bursts at window boundaries
- **Leaky bucket**: More complex implementation, similar performance

---

## Summary

### Key Patterns in Array-Based Solutions:

1. **Circular Buffers**: Efficient for time-series and streaming data
2. **Hash + Array**: Combines O(1) lookup with efficient storage
3. **Index Tracking**: Arrays with pointers for round-robin and LRU
4. **Fixed-Size Windows**: Predictable memory usage for real-time systems
5. **Batch Processing**: Array operations enable vectorization

### Performance Benefits:

- **Cache Locality**: Sequential memory access patterns
- **Predictable Memory**: Fixed-size allocations
- **Vectorization**: SIMD-friendly operations
- **Thread Safety**: Atomic operations on indices

### When Arrays Excel:

- **High-frequency operations** requiring constant time
- **Memory-constrained environments**
- **Real-time systems** needing predictable performance
- **Data processing** with regular access patterns
- **Systems programming** where control over memory layout matters

These examples demonstrate that arrays remain fundamental to high-performance software engineering, providing the foundation for scalable, efficient systems across various domains.

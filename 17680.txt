def solution(cacheSize, cities):
    execTime = 0
    cache = []
    # 캐시가 없을 경우
    if cacheSize == 0: return len(cities) * 5
    for city in cities:
      # cache hit
      if city.lower() in cache:
        cache.remove(city.lower())
        cache.append(city.lower())  # 해당 도시를 리스트의 맨 뒤로 보내기
        execTime += 1
      # cache miss
      else:
        if len(cache) == cacheSize: cache.pop(0)  # LRU 알고리즘으로 캐시 교체
        cache.append(city.lower())
        execTime += 5

    return execTime
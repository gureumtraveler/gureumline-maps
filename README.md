# 구름라인 스키장 지도 데이터 (gureumline-maps)

[구름라인(Gureum Line)](https://seokwoo.kim) 스키 기록 앱이 내려받는 국내 스키장 슬로프·리프트 데이터입니다.
OpenStreetMap에서 `piste:type`(슬로프), `aerialway`(리프트) 태그를 추출해 스키장별 GeoJSON으로 만들었습니다.

- 목록: [`manifest.json`](manifest.json) — 앱의 "스키장 지도 목록 URL"에 아래 주소를 넣으면 됩니다.
  ```
  https://raw.githubusercontent.com/gureumtraveler/gureumline-maps/main/manifest.json
  ```
- 스키장별 데이터: [`resorts/`](resorts)
- 데이터 상태: [`COVERAGE.md`](COVERAGE.md) — 스키장별 슬로프·리프트 수, 이름·난이도 태그 보유 현황

## manifest 형식

```json
{
  "version": "2026-11-12",
  "resorts": [
    { "id": "yongpyong", "name": "용평리조트", "bbox": [minLon, minLat, maxLon, maxLat],
      "overlay": "https://raw.githubusercontent.com/.../resorts/yongpyong.geojson",
      "pmtiles": null, "pistes": 41, "lifts": 20 }
  ]
}
```

`pmtiles`(오프라인 배경지도)는 아직 제공하지 않습니다. 추가되면 용량 때문에 GitHub Releases에 올리고 그 주소를 넣습니다.

## 갱신

생성 도구는 비공개 개발 저장소에 있습니다(`tools/maps/build_maps.py`). OSM 데이터가 바뀌면 다시 생성해 이 저장소를 갱신합니다.
슬로프 이름·난이도가 비어 있는 스키장은 OSM에 직접 보강하면 다음 갱신 때 반영됩니다.

## 라이선스

데이터 © [OpenStreetMap contributors](https://www.openstreetmap.org/copyright), [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/).
이 저장소의 데이터는 OSM에서 파생된 데이터베이스이므로 ODbL 조건(출처 표시, 동일 조건 공유)을 따릅니다.

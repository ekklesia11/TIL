# [TIL] react-native-svg-charts

---

리액트 네이티브에서 엑스포를 통해서 작업을 시작했다면 가능한 모듈과 사용이 불가능한 모듈들이 나뉠것이다. 예시는 보면 도움이 될 것 같다. Bar chart 예시다.

```react
import React from 'react';
import { View } from 'react-native';
import { BarChart, YAxis } from 'react-native-svg-charts';
import { Text } from 'react-native-svg';

class BarChart extends React.PureComponent {
  constructor() {
    super();
    this.state = {
      top5: []
    };
  }

  render() {
    const CUT_OFF = 50;
    const Labels = ({ x, y, bandwidth }) =>
      this.state.top5.map((v, index) => (
        <Text
          key={index}
          x={v.quantity < CUT_OFF ? x(v.quantity) + 10 : x(v.quantity) - 15}
          y={y(index) + bandwidth / 2}
          fontSize={14}
          fill={v.quantity >= CUT_OFF ? 'white' : 'black'}
          alignmentBaseline='middle'
        >
          {v.quantity}
        </Text>
      ));

    return (
      <View
        style={{
          flexDirection: 'row',
          height: 200,
          width: 250,
          paddingVertical: 16,
          marginLeft: 10
        }}
      >
        <YAxis
          data={this.state.top5}
          yAccessor={({ index }) => index}
          contentInset={{ top: 10, bottom: 10 }}
          spacingInner={0}
          formatLabel={(value, index) => {
            if (index % 2 === 0) {
              return this.state.top5[
                ((this.state.top5.length - 1) * 2 - index) / 2
              ].model;
            }
            return '';
          }}
          svg={{
            fontSize: 10,
            fill: 'black'
          }}
        />
        <BarChart
          style={{ flex: 1, marginLeft: 8 }}
          data={this.state.top5}
          horizontal={true}
          yAccessor={({ item }) => item.quantity}
          svg={{ fill: 'rgba(134, 65, 244, 0.8)' }}
          contentInset={{ top: 10, bottom: 10 }}
          spacingInner={0.5}
          spacingOuter={0}
          gridMin={0}
        >
          <Labels />
        </BarChart>
      </View>
    );
  }
}

export default BarChart;
```


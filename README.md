# React-Native-Axios
React Native Axios Get Data From API

[Axios Documentation](https://www.npmjs.com/package/axios)

Install Axios 
```
sudo npm install axios --save
```


```
import React from "react"
import { View, Text, TextInput, FlatList,YellowBox } from 'react-native'
import _ from 'lodash'
import axios from 'axios';

class BelajarAxios extends React.Component {
   state = {
       data: []
    
   }
   test = () => {
       if (_.isEmpty(this.state.data)) {
           alert('data ini kosong')
       }
       else {
           alert('data ini ada')
       }
   }
   renderItems = ({ item, index }) => {
       const {nama,kelas}=item
       return(
           <Text>{nama}</Text>

       )
   }

// Get Axios
componentDidMount() {
    axios.get(`http://mhs.rey1024.com/apibudaya/getListCategory.php`)
      .then(res => {
        const data = res.data;
        console.log(data);
        this.setState({ data });
      })
      .catch(err => consule.log(err))
  }

   render() {
    
    YellowBox.ignoreWarnings(['Encountered']);

       return (
           <View>
               <FlatList
                   data={_.take(this.state.data)}
                   keyExtractor={item => item.toString()}
                   renderItem={this.renderItems} />
               <Text onPress={() => this.test()}>TEST</Text>
           </View>
       )
   }
}
export default BelajarAxios
```

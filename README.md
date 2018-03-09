# NetInfo_Status
Here this is used to when we are having net connection fine other wise showing text

Step 1: 
First we have to Create Project like  react-native init SampleProject

Step 2: 
After we have to Create the OfflineNotice.js Component

like this below

import React, { PureComponent } from 'react';
import { View, Text, NetInfo, Dimensions, StyleSheet } from 'react-native';
const { width } = Dimensions.get('window');
function MiniOfflineSign() {
  return (
    <View style={styles.offlineContainer}>
      <Text style={styles.offlineText}>No Internet Connection</Text>
    </View>
  );
}
class OfflineNotice extends PureComponent {
  render() {
      return <MiniOfflineSign />;
  }
}
const styles = StyleSheet.create({
  offlineContainer: {
    backgroundColor: '#b52424',
    height: 30,
    justifyContent: 'center',
    alignItems: 'center',
    flexDirection: 'row',
    width,
    position: 'absolute',
    top: 30
  },
  offlineText: { 
    color: '#fff'
  }
});
export default OfflineNotice;

---------------------------------------------------

step 3:

Then where you want to setUp to Screen  or showing any page Please import to that screen 

import OfflineNotice from './OfflineNotice'


step 4: Now  import like this below

export default class App extends Component<{}> {
  render() {
    return (
      <View style={styles.container}>
        <OfflineNotice /> <---- add this here
        <Text style={styles.welcome}>Welcome to React Native!</Text>
        <Text style={styles.instructions}>To get started, edit App.js</Text>
        <Text style={styles.instructions}>{instructions}</Text>
      </View>
    );
  }
}



step 5:

Please take a  state varibale

constructor(props){
super(props)
state = {
    isConnected: true
};
}

step 6: 

function handleConnectivityChange = isConnected => {
    if (isConnected) {
      this.setState({ isConnected });
    } else {
      this.setState({ isConnected });
    }
  };

step 7  : here Net Info import from your react-native components

import { NetInfo } from 'react-native' 


Our componentDidMount should look like this:

componentDidMount() {
  NetInfo.isConnected.addEventListener('connectionChange', this.handleConnectivityChange);
}


Plus its also good practise to remove event listeners when your component is about to be unmounted to avoid any memory leakage, so we would do that in the componentWillUnmount lifecycle method.

componentWillUnmount() {
    NetInfo.isConnected.removeEventListener('connectionChange', this.handleConnectivityChange);

render() {
    if (!this.state.isConnected) {
      return <MiniOfflineSign />;
    }
    return null;
  }
Boom, that’s all there is to this. We have successfully created a “No Internet Connection” sign that responds to the state of the connection on your mobile device.



The final OfflineNotice.js component should look like this: 
Please check the Js file OfflineNotice.js 
 }



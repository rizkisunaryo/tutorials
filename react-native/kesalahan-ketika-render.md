# Salah
```
render() {
    let img = this.props.show ?  ( 
        <Image 
            source={{uri:'https://link.to/image.jpg'}}
            style={{width:100, height:100}}
            resizeMode='contain' />
    ) : (<View></View>);
    
    return (
        <View>{img}</View>
    );
}
```

# Salah

```
render() {
    let uri = '';
    let width = 0;
    let height = 0;
    if (this.props.show) {
        uri = 'https://link.to/image.jpg';
        width = 100;
        height = 100;
    }
    
    return (
        <View>
            <Image source={{uri}} style={{width,height}} 
                resizeMode='contain' />
        </View>
    );
}
```

# Benar
```
constructor(props) {
    super(props);
    this.state = {
        uri: '', 
        width: 0, 
        height: 0, 
    }
}

_showOrHide(show) {
    let uri = '';
    let width = 0;
    let height = 0;
    if (show) {
        uri = 'https://link.to/image.jpg';
        width = 100;
        height = 100;
    }
    this.setState({uri, width, height});
}

componentDidMount() {
    this._showOrHide(this.props.show);
}

componentWillReceiveProps(nextProps) {
    if (this.props.show !== nextProps.show)
        this._showOrHide(nextProps.show);
}

render() {
    return (
        <View>
            <Image source={{this.state.uri}} 
                style={{width:this.state.width, 
                    height:this.state.height}}
                resizeMode='contain' />
        </View>
    );
}
```


No skills worth mentions, zero,zip,zilch,nada. But for the fun of it heres some very ugly code i wrote awhile ago.

    import React from 'react'
    import VideoPlayer from './components/video-player'
    import axios from 'axios'
    const initalVideo = 'Code-Monkey'
    const arrOfColorsForPubliserImg = ['red','yellow','pink','purple','orange','silver']

    class App extends React.Component{
      constructor (props){
        super(props)

    this.state = {
      videoName: initalVideo,
      videoKey:1,
      numberOfViews: 3029417,
      dateOfCreation: 'Jul 4, 2007',
      likes: 24000,
      dislikes: 543,
      videoDescription: 'This AMV features the song Code Monkey by Jonathan Coulton, using footage from the anime Black Heaver.',
      publisher: 'Nic Neidenbach',
    }
    this.changeVideoSrc = this.changeVideoSrc.bind(this)
    }
    async changeVideoSrc(videoKey){
    
    await axios.get(`http://localhost:3201/db/${videoKey}`)
    .then(res =>{

      this.setState({
      videoName: res.data.name,
      videoKey: videoKey,
      numberOfViews: res.data.view_count,
      dateOfCreation: res.data.created_on,
      likes:res.data.likes,
      likes:res.data.dislikes,
      videoDescription: res.data.discription,
      publisher:res.data.publisher
    })
    })
    }

    componentDidMount(){
    window.addEventListener('changeVideoKey',(e)=>{
      this.changeVideoSrc(e.detail.videoKey)})
    }
    render(){
    
    let displayVideoName = this.state.videoName.split('-').join(' ')
    let displayNumberOfViews = parseInt(this.state.numberOfViews)
    return(
      <div id='videoPlayerContainer'>
        <VideoPlayer
          key={this.state.videoKey}
          videoName={this.state.videoName}
          previousVideoName={this.state.previousVideoName}
          />
        <div id='videoPlayerFooter'>
          <div id='videoPlayerFooterLeft'>
            <p id='nameOfVideo'>{displayVideoName}</p>
            <p id='numberOfViews'>{displayNumberOfViews} Views * {this.state.dateOfCreation}</p>
          </div>
          <div id='videoPlayerFooterRight'>
            <div id='innerVideoPlayerFooterRight'>
              <p id='likeAndDislike'><i className='fas fa-thumbs-up'></i>  {this.state.likes}</p>
              <p id='likeAndDislike'><i className='fas fa-thumbs-down'></i> {this.state.dislikes}</p>
              <button id='videoShareBtn'>Share</button>
              <button id='videoSaveBtn'>Save</button>
              <button id='videoMoreBtn'>...</button>
            </div>
          </div>
        </div>
        <hr id='videoHr'></hr>
          <div id='publisher'> 
            <div id='publisherImg'></div>
            <div id='publisherInfo'>
              <p id='publisherName'>{this.state.publisher}</p>
              <p id='publisherSubCount'>{Math.floor(Math.random() * 1000000)} Subscribers</p>
            </div>
          </div>
          <p id='videoDescription'>{this.state.videoDescription}</p>
      </div>
    )
     }
    }

    export default App;
## The links to these other pages and what they have are as follows:


  1. [Life events leading up to now](readme2.md "Be prepared")
  2. [Job experince](readme3.md "Hopefully will add more soon")
  3. [Home page](README.md "back to the start")
  4. [other ways to contact me](readme5.md "Reach out to me")








----------------------------------------------
- [Dont click me](https://www.youtube.com/watch?v=dQw4w9WgXcQ "Warning you") <img src="https://media.istockphoto.com/photos/yellow-background-with-black-grunge-danger-sign-picture-id1163744382?k=20&m=1163744382&s=612x612&w=0&h=jM9nrlT8ELvXEWwsB6vA8gwGc3xPC-RHdosyagPixfc=" alt="DANGER" style="height: 50px; width:100px;"/>

---
title: 'Class Component'
date: '2020-01-02'
type: programing
---

# ReactJS Class Component



```javascript

// ./src/CatDescription.tsx

import React from 'reat';

interface IProps{
	likeBy?: number
}

interface IState{
	like: number;
}

class CatDescription extends React.Component<IProps, IState>{
	public static defaultProps: Partial<IProps> = {
		likeBy: 1,
	};
	
	public state: IState = {
		like: 0
	};
	
	public increase = () => {
		const likeBy: number = this.props.likeBy!;
		const like = this.state.like + likeBy;
		this.setState({ like });
	};
	
	public render(): React.ReactNode{
		return (
			<div>
				<p> Hello ... it's me.</p>
				<img src="https://i.imgur.com/igdestH.gif" alt="cat image" />
				<button onClick={this.increase}> Likes: {this.state.like}</button>
			</div>
		);
	}
}

export default CatDescription;

```


---
Tags: [[ReactJS Class Component]], [[ReactJS Component]] 
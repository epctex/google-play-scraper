# Actor - Google Play Scraper

## Google Play scraper

Since Google Play doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Google Play data scraper supports the following features:

-   Get all the reviews instantly - You can search any keyword you would like to have and get the results

-   Any language, any region - Scrape any list that you'd like to get from Google Play

-   Search any keyword - You can search any keyword you would like to have and get the results

-   Get all apps from any developer - You can check the shelves and scrape the information of the newest updates.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/google-play-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Google Play that should be visited. Required fields are:

| Field                | Type    | Description                                                                                                                                                                                                    |
| -------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| startUrls            | Array   | (optional) List of Google Play URLs. You should only provide search, developer page, or  application page URLs.                                                                                                                 |
| includeReviews       | Boolean | (optional) This will add all the reviews that Google Play provides into the app objects. Please keep in mind that the time and resources the actor uses will increase proportionally by the number of reviews. |
| endReviewsPage              | Integer | (optional) Final number of reviews page that you want to scrape. Default is `Infinite`. This only limits out the reviews pages.                                                          |
| proxy                | Object  | Proxy configuration                                                                                                                                                                                            |

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

##### Tip

If you want to scrape reviews of an application which contains a lot, using `endReviewsPage` is strongly suggested. Even though the actor has the capability to scrape all of them, the total resource consumption will proportionally increase and might be too much.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detail requests. If actor doesn't block very often it'll scrape 100 apps in less than a minute with ~0.001-0.003 compute units.

### Google Play Scraper Input example

```json
{
  "startUrls":[
    "https://play.google.com/store/search?q=hello&c=apps&hl=tr&gl=US",
    "https://play.google.com/store/apps/developer?id=Mattel163+Limited",
    "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&hl=tr&gl=US"
  ],
  "includeReviews":true,
  "endReviewsPage":1,
  "proxy":{
    "useApifyProxy":true
  }
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Google Play Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Google Play actor.

## Scraped Google Play Properties

The structure of each app in Google Play looks like this:

### App Detail

```json
{
	"title": "Hello Neighbor",
	"description": "Hello Neighbor is a stealth horror game about sneaking into your neighbor's house to figure out what horrible secrets he's hiding in the basement. You play against an advanced AI that learns from your every move. Really enjoying climbing through that backyard window? Expect a bear trap there. Sneaking through the front door? There'll be cameras there soon. Trying to escape? The Neighbor will find a shortcut and catch you.",
	"descriptionHTML": "Hello Neighbor is a stealth horror game about sneaking into your neighbor&#39;s house to figure out what horrible secrets he&#39;s hiding in the basement. You play against an advanced AI that learns from your every move. Really enjoying climbing through that backyard window? Expect a bear trap there. Sneaking through the front door? There&#39;ll be cameras there soon. Trying to escape? The Neighbor will find a shortcut and catch you.",
	"summary": "Stealth Horror game with adaptive AI",
	"installs": "10,000,000+",
	"minInstalls": 10000000,
	"maxInstalls": 48440220,
	"score": 3.9681275,
	"scoreText": "4.0",
	"ratings": 478217,
	"reviews": 18775,
	"histogram": {
		"1": 82934,
		"2": 22186,
		"3": 27670,
		"4": 39775,
		"5": 305616
	},
	"price": 0,
	"free": true,
	"currency": "USD",
	"priceText": "Free",
	"available": true,
	"offersIAP": true,
	"IAPRange": "$0.99 - $14.99 per item",
	"androidVersion": "6.0",
	"androidVersionText": "6.0",
	"developer": "tinyBuild",
	"developerId": "4988311280735374056",
	"developerEmail": "support@tinybuild.com",
	"developerWebsite": "http://tinybuild.com",
	"developerAddress": "3831 152nd PL SE\nMill Creek, WA, 98012\nUSA",
	"privacyPolicy": "http://www.tinybuild.com/privacy-policy",
	"developerInternalID": "4988311280735374056",
	"genre": "Adventure",
	"genreId": "GAME_ADVENTURE",
	"icon": "https://play-lh.googleusercontent.com/aDX4QRdSBmlOTeWAsS5NbKcggupZ6_RSUzz7kLyIY91RChNDvEv26Czcqb-1rgt6FeE",
	"headerImage": "https://play-lh.googleusercontent.com/AV7riRXVt0hX_IEEp2K2bY3_VWOFjs-FYSb4TxA2_pSeAGiS2s7lozrctx6rxtQjdPc",
	"screenshots": [
		"https://play-lh.googleusercontent.com/RFqqm8516bdg1FZhAQtGCsScKZdK9FD_DaiDvdwh7woDxLkKfYv6IPyA-zqSvgSv9A",
		"https://play-lh.googleusercontent.com/LvefSGsK3WG_o9KcioUX4dles_LydRSbeRMi6mvodG_ql1cLpmc5EoWl26d7XXNMrag",
		"https://play-lh.googleusercontent.com/TKiYF5jqhqD6HNDLOqn1z80cATwxS4qrxFfJppyxTyeitiAQ1WejyYgdfyXhwzkMaX8",
		"https://play-lh.googleusercontent.com/qXBsiI19vsbhySt-2vRYxWUttzEHv8wlSgGpdq8grr4qlPLWaRSc-O9STn0H50Qi47A",
		"https://play-lh.googleusercontent.com/Mve7R6D1rJLt8hBRxbLnhxjUJdW5spXwyHi7NfAHdQY6ZX-DYsUnPppIgoOPF_qqr0w",
		"https://play-lh.googleusercontent.com/kULYRuQA3_KVylqhw7FD6-C3L0ylg0m21aJNlzkMwtYOSMqQBDjpUAjDjG6BVL0RBoQ",
		"https://play-lh.googleusercontent.com/6SXwYiMgIhQE23T2WzMNlX5-ZqoJOJKNA8seUZwus87vbmEnTkbfNBMyrlpvu2W3ypo",
		"https://play-lh.googleusercontent.com/HncFaPa7BMkOAJVrhWRNid1PqxuRcAxePcikCv9UprAUjxHbZpqNV7Xo3GKSdCIQOA",
		"https://play-lh.googleusercontent.com/rKhbmcWjILToV6FDUeMj5eIZPo7c9pCwqx0hSKMZyngsHsFOuIRuUuEHns_i_UjbZ1E",
		"https://play-lh.googleusercontent.com/V5DdhLxPFqaNYEtVx_ALhdU0l_MUzW_QdHzxG_XuDyVczrbEN_6ADgV59zCAJRQ9mw",
		"https://play-lh.googleusercontent.com/1SsWfBW7sIalzq6GFh98elYpdEZPpqWeapzFQp85QbleCt1paakE4jnKurEkk3zvHQ",
		"https://play-lh.googleusercontent.com/-45PcLhwZAUNrhsvpI_cHaaaWLcEe46wq7CoZBtRO1Tfdd23sN0yjlLdM144VAmKjXNv",
		"https://play-lh.googleusercontent.com/IM8C1ORsa6lxCOZVZ0RZKZvzkNc4Xs3qfdz7ViKvcrO-vIDY4qd3Heiq-BMiXXqZoZY",
		"https://play-lh.googleusercontent.com/jOjkrWwnWbHUXIufE4WBtnocEnuhmMKQjlDvafqhKuPjCyqyqCgBPTciVBkvJAIa_g",
		"https://play-lh.googleusercontent.com/ycaBWh2N7IQCuh8yxy9pmMUju6j7edjcZGSo2Aqw8K2z_tI8AWmzCmy8UW7hBM4gY50",
		"https://play-lh.googleusercontent.com/w_n8Z1ydO5umzo8ALqbH1KTlSRM6UdJHJiM3FB7yYstAdIdwRs4-cPxfzD2ZJqSFs-U",
		"https://play-lh.googleusercontent.com/bxq49B5x8en2_xEwN81POlFR8_qiCqu2ybBgArvJLK2CYk72RBytxI2_dn8jdsc-_67f",
		"https://play-lh.googleusercontent.com/yKFihAmePJ0OzLfraOQc5MgZ7rxXavc0UjHTaAwbwGqNI8H05ZNMrZWpWQtmhklHgYE",
		"https://play-lh.googleusercontent.com/kvuveeX1_CFUZreyFpCn1whf91mmbukKKDgpwSl_yt_NHQEwyqiMIxpBjrIQN0J7GA",
		"https://play-lh.googleusercontent.com/Zs8YeeUR6IUFDUdWg8IAxgxusrZoQASDShSi7UgJg2g6PlmaZQC6cHEKooZQInkTGw",
		"https://play-lh.googleusercontent.com/KZJACnUY3IM2BnvnbVt0-_mupEhXzOxynUU8LAGw6bilhwGhmvusFJPajicdNjGqh38",
		"https://play-lh.googleusercontent.com/eBL1A2FNjp_I3ADJJxd7ghwj9XvUbNlZ8AbdAyl-5e0e7JEoAuNnw3SkirnrVigEG4Q",
		"https://play-lh.googleusercontent.com/U-eT0uIYDrn7Bvml3WJ_RdnJM4IhxM7s9prB3ri1oHM1XJvMUfokzP0X7wJ0Rb32CgUL",
		"https://play-lh.googleusercontent.com/kgfAjQbjpWLRhVkCwnxeh-eIlQr6v3wu63_29d4g5aGh1UsvOrjTBjXWlMKGmgJwhkOd"
	],
	"video": "https://www.youtube.com/embed/qGUUPM2rwr4?ps=play&vq=large&rel=0&autohide=1&showinfo=0",
	"videoImage": "https://play-lh.googleusercontent.com/AV7riRXVt0hX_IEEp2K2bY3_VWOFjs-FYSb4TxA2_pSeAGiS2s7lozrctx6rxtQjdPc",
	"contentRating": "Everyone 10+",
	"contentRatingDescription": "Mild Violence",
	"adSupported": false,
	"released": "Jul 25, 2018",
	"updated": 1655681702000,
	"version": "1.0",
	"recentChanges": "Bugfixes and stability improvements",
	"comments": [
		null,
		null,
		null,
		null,
		null
	],
	"appId": "com.tinybuildgames.helloneighbor",
	"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&hl=en&gl=US",
	"reviewsList": [
		{
			"id": "9c0b61d6-0f53-4e45-a6ad-9f37d23dc240",
			"userName": "Sourav Kayal",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCkgTeA1rC7eOdjlhho6H_UDn1956LFBTfs9UdN4",
			"date": "2023-01-18T08:42:04.509Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=9c0b61d6-0f53-4e45-a6ad-9f37d23dc240",
			"title": null,
			"text": "My favourite game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_tile_matching",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_stick_figure",
					"rating": 1
				},
				{
					"criteria": "vaf_games_single_player",
					"rating": 1
				}
			]
		},
		{
			"id": "1a0a9dcf-db0c-46f0-9707-bcc880281e40",
			"userName": "Ammar Hussain",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCluvdVsDyHSY_hT1tAccmmzNDqABjhSjgBlxpn4wQ",
			"date": "2023-01-18T08:30:02.105Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=1a0a9dcf-db0c-46f0-9707-bcc880281e40",
			"title": null,
			"text": "It is, a challenging & horror game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "b86a51b1-447e-45fe-aa40-c76195ac34dd",
			"userName": "Md.Arafat Hossain",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCk_WwAXyBUTBPjD5edoVrCH5d_bp40xV7MsmwFr",
			"date": "2023-01-18T07:31:52.613Z",
			"score": 3,
			"scoreText": "3",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=b86a51b1-447e-45fe-aa40-c76195ac34dd",
			"title": null,
			"text": "I think it's a high graphic game so it's impossible to run on low budget mobile phone so I think if the is available on Microsoft store so it can be played on PC. So everyone can play this game 🎮. I hope soon this game will be release on Microsoft store.",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "06415328-4013-4581-a589-f2a2e90a5894",
			"userName": "nitu Rathore",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6zmWYwrUmbxlfI1B7ZdvkuL5IjSP-nJgKv0ld2=mo",
			"date": "2023-01-18T06:51:44.710Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=06415328-4013-4581-a589-f2a2e90a5894",
			"title": null,
			"text": "Achcha game 87 MB ka kar do",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "0a682827-afbc-4ca0-a627-aef0d1d997e5",
			"userName": "Komal Kashmiri",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6_zcVrBc8o9blZTCJowY7yHaxFW_eJY_Tj8R0G=mo",
			"date": "2023-01-18T06:50:38.167Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=0a682827-afbc-4ca0-a627-aef0d1d997e5",
			"title": null,
			"text": "Best 👍👍👍 game 🎮",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_fighting",
					"rating": 1
				},
				{
					"criteria": "vaf_games_silly",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_tank",
					"rating": 1
				}
			]
		},
		{
			"id": "e2a4ff90-46e2-4d9c-a83f-d44ac54c2b13",
			"userName": "Abhranil Das",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCkE8Uldm8t56lesvh8SAmwmqL03C2VUDmPHO5GDIg",
			"date": "2023-01-18T04:41:32.903Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=e2a4ff90-46e2-4d9c-a83f-d44ac54c2b13",
			"title": null,
			"text": "Very nice game and all look and graphics quality 😍😍 amazing",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "17fb6fef-a0a8-4dbd-99e8-c966368979c8",
			"userName": "Kajal Shlke",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5D3t-YHo-n1w_ksywSs2OK_cFcAMsgPzcB61p6=mo",
			"date": "2023-01-18T04:23:50.723Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=17fb6fef-a0a8-4dbd-99e8-c966368979c8",
			"title": null,
			"text": "Hello night to apply",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "17603803-be10-4dfd-87d3-98fff168cdbe",
			"userName": "Zareena B",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6xNd7ZKZaAABLEoBwFADJFx_SYyjQh_GNm5mY=mo",
			"date": "2023-01-18T04:10:33.250Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=17603803-be10-4dfd-87d3-98fff168cdbe",
			"title": null,
			"text": "I love this game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "2516d7bd-4a54-4ffc-b524-c4438889770f",
			"userName": "Ahmad Shaikh",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4oj74uwGpYFlG1jkbbhpMKd4XP2LpugeYR4B9_=mo",
			"date": "2023-01-18T04:02:00.343Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=2516d7bd-4a54-4ffc-b524-c4438889770f",
			"title": null,
			"text": "Op game it is very difficult",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "98e43c1c-2d85-4f09-9f59-e65bd84fffc5",
			"userName": "mondal milan",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCkzx7CHY3chUWUYdWOilQASX5Y-B_Ob4hhY-CAs_g",
			"date": "2023-01-18T03:49:30.867Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=98e43c1c-2d85-4f09-9f59-e65bd84fffc5",
			"title": null,
			"text": "1 star reason we can't save this game please udate and save option enable",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "5118b4a2-0ce9-40ed-a37d-99a55bbdd40a",
			"userName": "Sachchida Nand gupta",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCkUGDZGsydp1rZc5w-A34RZiINc8tI-X8EAszggLg",
			"date": "2023-01-18T02:08:30.930Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=5118b4a2-0ce9-40ed-a37d-99a55bbdd40a",
			"title": null,
			"text": "Very nice",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_hidden_object",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_car",
					"rating": 2
				},
				{
					"criteria": "vaf_games_classic",
					"rating": 1
				}
			]
		},
		{
			"id": "cee91cc9-5533-4b6a-83ad-11c260f23ae7",
			"userName": "Apurba sinha ,5,Sigma",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClNUeqXvmMrystiT6CNmLu6f6Krb4wIuVW7tyKiDw",
			"date": "2023-01-18T02:06:36.627Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=cee91cc9-5533-4b6a-83ad-11c260f23ae7",
			"title": null,
			"text": "Excellent",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "94f8a89b-6a58-46b2-9b6a-4ea59d82e7b3",
			"userName": "ezrah martinez",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5QHwx_NPuJ4dFxQEkOobSjZLLqPuXplzyMyDoW=mo",
			"date": "2023-01-18T00:41:08.357Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=94f8a89b-6a58-46b2-9b6a-4ea59d82e7b3",
			"title": null,
			"text": "its so fun bth",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_memory",
					"rating": 1
				},
				{
					"criteria": "vaf_games_single_player",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_motorcycle",
					"rating": 2
				}
			]
		},
		{
			"id": "9e26c84b-01c7-4584-830f-0827c2b3ca1a",
			"userName": "Emma Chatters",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCnC7wLoOmMIUFy88EWh4MLyvWG2RA5Xrh-JEMDDyw",
			"date": "2023-01-18T00:02:59.266Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=9e26c84b-01c7-4584-830f-0827c2b3ca1a",
			"title": null,
			"text": "Please don't play hello neighbor it is really scary to play",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "5f674cf6-d156-48cc-8187-e430bf822471",
			"userName": "Nicholas Benally",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5v-eeJcsS9IntCxYQWd6U-5sHFovcO4Yq_yHtq=mo",
			"date": "2023-01-17T22:40:57.572Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=5f674cf6-d156-48cc-8187-e430bf822471",
			"title": null,
			"text": "You can't go to the thousand mat",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "62b2cd01-0089-44cd-96d7-f641cce35616",
			"userName": "tevita lutui",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6cGxz7Nr0fOoWV5cOoAGBcGmv4-NIBUCOuNpia=mo",
			"date": "2023-01-17T21:52:36.255Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=62b2cd01-0089-44cd-96d7-f641cce35616",
			"title": null,
			"text": "I do love it,it scares me and you get to play act 1 for free",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_minigames",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_solitaire",
					"rating": 3
				},
				{
					"criteria": "vaf_games_works_offline",
					"rating": 3
				}
			]
		},
		{
			"id": "39cf760c-ae41-440b-acf1-3c9733524cc8",
			"userName": "BiBi Sabzadgai",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5m34L9gZwCXysE0c2tPm4G208kqxRGrWfrnx1f=mo",
			"date": "2023-01-17T21:14:05.765Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=39cf760c-ae41-440b-acf1-3c9733524cc8",
			"title": null,
			"text": "Very fun game definitely would play again",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "2d0d003a-6c97-4024-9d0a-ce4b42a34774",
			"userName": "Deepakshiva Kumar",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClIC8UC56aaPp0EBrNOt4GX6aaTzyazhNFMjoBW",
			"date": "2023-01-17T18:53:20.607Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=2d0d003a-6c97-4024-9d0a-ce4b42a34774",
			"title": null,
			"text": "T ho na ho na hi",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "e8de815a-41b4-45f9-b136-37e65c17a7cc",
			"userName": "Serj Ga",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCktWCcH2ykIu0qoEw4biJPjH9wFR_JJRoQB5DpoecM",
			"date": "2023-01-17T17:36:09.232Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=e8de815a-41b4-45f9-b136-37e65c17a7cc",
			"title": null,
			"text": "I past all seasons best game ever",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "7470eb84-a69c-40dd-b6fe-836e78a9919b",
			"userName": "ata Gee",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCmxb3_fv2YiSDEWKEHGPhZky53CdyntutPOUSz4_Q",
			"date": "2023-01-17T16:12:08.949Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=7470eb84-a69c-40dd-b6fe-836e78a9919b",
			"title": null,
			"text": "I played this game but it was really hard to trust it But it was a fun to play this game forever I play this game I just install this game And it was really That I was good it is my small comment for This game I really enjoy thank you",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "3fcd47f8-a1db-41fc-bd70-f16bd81b301f",
			"userName": "Abbash Khan",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7kYcWC_YyxYLxFyzV_oCslMbvNsjF52Nd0Pm3g=mo",
			"date": "2023-01-17T16:09:50.887Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=3fcd47f8-a1db-41fc-bd70-f16bd81b301f",
			"title": null,
			"text": "Best game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "b2983284-273c-4d5f-8c9f-3568017be907",
			"userName": "Rashmi",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClOZtuwWrQqBXjPeHvh3UOqXCNmHjrLrRlWvFja",
			"date": "2023-01-17T16:08:57.482Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=b2983284-273c-4d5f-8c9f-3568017be907",
			"title": null,
			"text": "V.good",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_shooting_gallery",
					"rating": 2
				},
				{
					"criteria": "vaf_never_display_difficult_to_use",
					"rating": 2
				},
				{
					"criteria": "vaf_games_entertaining",
					"rating": 1
				}
			]
		},
		{
			"id": "366c9f6b-90dc-49ba-9f63-ad0d7ee7b4c7",
			"userName": "Stephanie Guardado",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4gJ3vuGNfpZdE5PgipWhUwarxr4lxcCgVP-SxE=mo",
			"date": "2023-01-17T13:49:35.734Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=366c9f6b-90dc-49ba-9f63-ad0d7ee7b4c7",
			"title": null,
			"text": "Its so fun",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_subject_boating",
					"rating": 2
				},
				{
					"criteria": "vaf_games_genre_number",
					"rating": 2
				},
				{
					"criteria": "vaf_games_addictive",
					"rating": 2
				}
			]
		},
		{
			"id": "f28e8372-0f0b-4f33-abc5-934c890bfe47",
			"userName": "A7mad Boudi",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7ANS42EASDx05FOKF7L8yT3B0Nt0ZbhoXlCCEb=mo",
			"date": "2023-01-17T13:24:17.797Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=f28e8372-0f0b-4f33-abc5-934c890bfe47",
			"title": null,
			"text": "تتبهيتبننط",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ae997ee9-c93d-43df-9956-80330bd138ff",
			"userName": "Hardeep Singh",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp75jHnhK0MUguAHS_vahixcHrylfklozNjrlD73=mo",
			"date": "2023-01-17T13:10:44.700Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ae997ee9-c93d-43df-9956-80330bd138ff",
			"title": null,
			"text": "Is world ki sabse best game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "3247a6d2-4bd2-4d44-a470-ec29e51909be",
			"userName": "Mahendra SHETYE",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6ngWRACxwd9_4KAbfKuZCGui4-9sbtzHOH6wE=mo",
			"date": "2023-01-17T12:53:53.414Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=3247a6d2-4bd2-4d44-a470-ec29e51909be",
			"title": null,
			"text": "A very nice game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_life_simulation",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_parking_simulation",
					"rating": 2
				},
				{
					"criteria": "vaf_games_classic",
					"rating": 2
				}
			]
		},
		{
			"id": "f73cb7e0-c9d2-4b34-bf82-d5ad9ee5d409",
			"userName": "mowsumi rahman",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6hhpHM5PRW75-UJJvClN2vXvQ3xIWS5sNRSkcq=mo",
			"date": "2023-01-17T12:25:57.524Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=f73cb7e0-c9d2-4b34-bf82-d5ad9ee5d409",
			"title": null,
			"text": "I like it",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ab0456b7-a24c-450d-b884-d04cc29572c2",
			"userName": "Anwar Basha",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5HsRwmxYDSUGAnDZCgjIl76b1cxLKJHcqAeOO_=mo",
			"date": "2023-01-17T11:22:05.785Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ab0456b7-a24c-450d-b884-d04cc29572c2",
			"title": null,
			"text": "Hello my neighbor",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "f4b927d4-f779-4dd6-bf77-dce726ba4204",
			"userName": "Divakar Guru",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp53cPlZ3ccqNY7Vo7cSc4qhRFfYaSOKn449gkzz=mo",
			"date": "2023-01-17T10:28:36.842Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=f4b927d4-f779-4dd6-bf77-dce726ba4204",
			"title": null,
			"text": "My favourite game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "22ccd8a8-81ca-45ab-a69b-8603fa085866",
			"userName": "Makeda Sarah",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCmBFIuAY3KZoJlIFfMsm9gcUt_e3b5vCyVLHjBK",
			"date": "2023-01-17T10:24:13.749Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=22ccd8a8-81ca-45ab-a69b-8603fa085866",
			"title": null,
			"text": "I love this game so much it was so fun I hope this game get update soon I really really really love this game so so much",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "fc601d5f-f5d0-4d3c-8ab5-3bc0ecc35642",
			"userName": "Ch Amal",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCmKFEZ77yTxprT2dBJyoCXAMqhxbFlx8tATZPaof-U",
			"date": "2023-01-17T08:51:31.678Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=fc601d5f-f5d0-4d3c-8ab5-3bc0ecc35642",
			"title": null,
			"text": "Its so fun i am giving four star bc its so scary to go in the house and its the only way you can escape lol so anyway its perfectly made",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_quiz",
					"rating": 2
				},
				{
					"criteria": "vaf_games_subject_boating",
					"rating": 2
				},
				{
					"criteria": "vaf_never_display_difficult_to_use",
					"rating": 1
				}
			]
		},
		{
			"id": "5044f748-bfb8-4259-9c43-bc031128da3e",
			"userName": "Jogmaya Nath",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4qVqOYjQK6JRVU0PSUjKZMLk5znnGnRoYI3L_O=mo",
			"date": "2023-01-17T08:21:45.376Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=5044f748-bfb8-4259-9c43-bc031128da3e",
			"title": null,
			"text": "Bad game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_subject_motorcycle",
					"rating": 2
				},
				{
					"criteria": "vaf_games_genre_quiz",
					"rating": 2
				},
				{
					"criteria": "vaf_never_display_content_language",
					"rating": 2
				}
			]
		},
		{
			"id": "e42169bd-002c-4405-98c6-1499bdcea796",
			"userName": "NARESH JAGLAN",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5oR0r9pvweY31J7Nqo_8RgwxU5clYWMUyRlqNL=mo",
			"date": "2023-01-17T08:10:15.782Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=e42169bd-002c-4405-98c6-1499bdcea796",
			"title": null,
			"text": "This is Avery good horror game. The graphics are good.there are some much places to explore. Please make hello neighbour 2 . More horror then this. We play this best horror game on playstore. No one can't say this is a bad game. This is avery good game for mobile. All people do not have pc so they can enjoy this best game on mobile. This is a very good thing. Thank you so much to make this game for mobile.",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_ball",
					"rating": 2
				},
				{
					"criteria": "vaf_games_subject_drift_racing",
					"rating": 2
				},
				{
					"criteria": "vaf_games_cute",
					"rating": 2
				}
			]
		},
		{
			"id": "c6af2e28-8925-4d89-a5cf-72fa7a5781a2",
			"userName": "Manju Suwalka",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6k5UbQAV9jNqozGbj7XUk4uaDnzw6woaJxFvZS=mo",
			"date": "2023-01-17T07:33:18.399Z",
			"score": 3,
			"scoreText": "3",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=c6af2e28-8925-4d89-a5cf-72fa7a5781a2",
			"title": null,
			"text": "It is too hard i cant compelete these acts but its good for gamers",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "de660de1-d71c-4b03-b89d-bbb2e3301c85",
			"userName": "Zeke Martinez",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4fQvnfMVgmpmT4VJRvSYRrRPaxRtBJmGhuXs3hdw=mo",
			"date": "2023-01-17T05:06:19.198Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=de660de1-d71c-4b03-b89d-bbb2e3301c85",
			"title": null,
			"text": "Barely has a single ad.",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "b88e5445-8e6e-4d51-b7bc-b4d11fdbed69",
			"userName": "Mahendra Meena",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5BvOZoGXwTwhoADw1Y7R6uDCvEVyFvoPwaR2LR=mo",
			"date": "2023-01-17T04:41:21.633Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=b88e5445-8e6e-4d51-b7bc-b4d11fdbed69",
			"title": null,
			"text": "RAX GANMAG .009",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ba032a0c-5161-4fcb-99b6-5f92e3b523ae",
			"userName": "AJC MOM&SONS",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4z-xcQ2z3Jibd1PBP6Nc3_mqiKslDiw4C689U3=mo",
			"date": "2023-01-17T04:33:29.433Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ba032a0c-5161-4fcb-99b6-5f92e3b523ae",
			"title": null,
			"text": "tip: i f you want to go to the basement is get 2 boxes place it on a ladder dont forrget 1 item 2 shoot the window get the painting and get the red key and connect it to the trunk",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "4a170ae7-dd6e-4109-b799-38d0979a28c4",
			"userName": "Danielle Hanson",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp76khvE0hYs19y2mle6ghVp1Th_KtedsGlVLPGP=mo",
			"date": "2023-01-17T01:31:56.457Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=4a170ae7-dd6e-4109-b799-38d0979a28c4",
			"title": null,
			"text": "There is nothing wrong with it I'm 10",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "91fa566c-c0ff-4d6c-88fb-36133ba17279",
			"userName": "Kiran Bisht",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7vXG_EtIpomFRhedLBsN2H42mzvlrJd5f2Eg=mo",
			"date": "2023-01-17T01:23:52.475Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=91fa566c-c0ff-4d6c-88fb-36133ba17279",
			"title": null,
			"text": "It is the game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "cd73e0d9-9cbc-440e-ac8b-fba4040318f2",
			"userName": "Robert",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7rGujmRrvm057P0olj2-C5Ao6yZodsFLgvbyeK=mo",
			"date": "2023-01-16T23:28:43.283Z",
			"score": 2,
			"scoreText": "2",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=cd73e0d9-9cbc-440e-ac8b-fba4040318f2",
			"title": null,
			"text": "I can't look any other direction other than straight Infront of me",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "4ffdd6a7-dd7a-41c9-9855-8c83f779a013",
			"userName": "Yesica Aguilar",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5fhFKfv_RNN_m2cs-Ya0DsTg4cAoZeg3jJCHEy=mo",
			"date": "2023-01-16T21:00:06.686Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=4ffdd6a7-dd7a-41c9-9855-8c83f779a013",
			"title": null,
			"text": "Lakaka",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_beautiful",
					"rating": 1
				}
			]
		},
		{
			"id": "1b2afc33-13ca-4644-b5a6-d7ff6ad71841",
			"userName": "A Google user",
			"userImage": "https://play-lh.googleusercontent.com/EGemoI2NTXmTsBVtJqk8jxF9rh8ApRWfsIMQSt2uE4OcpQqbFu7f7NbTK05lx80nuSijCz7sc3a277R67g",
			"date": "2023-01-16T20:09:38.365Z",
			"score": 2,
			"scoreText": "2",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=1b2afc33-13ca-4644-b5a6-d7ff6ad71841",
			"title": null,
			"text": "I don't know why I had to pay 15 pounds for act 2 and 3",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "46b21625-9ccf-4019-bb08-1b901920a4ab",
			"userName": "Kiran Yassar",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6lB9WsOOGtx1rLxaC3ZPwuwR_heWQC5NKMMInJ=mo",
			"date": "2023-01-16T19:40:22.979Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=46b21625-9ccf-4019-bb08-1b901920a4ab",
			"title": null,
			"text": "I love it because it's a puzzle game and horror",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_puzzle",
					"rating": 3
				},
				{
					"criteria": "vaf_games_subject_parking_simulation",
					"rating": 2
				},
				{
					"criteria": "vaf_games_simple",
					"rating": 3
				}
			]
		},
		{
			"id": "590083e2-87f3-4615-97bd-9b98b51f030f",
			"userName": "Caleb Parsons",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6ltebHFy3hvkWIlPTPoP3SRE8cbjq5_X4cBjQH=mo",
			"date": "2023-01-16T17:36:50.340Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=590083e2-87f3-4615-97bd-9b98b51f030f",
			"title": null,
			"text": "its not letting me even start up the game",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "a2a38169-6784-4f42-8933-cc78c10bee2c",
			"userName": "Lillie McGaha",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5VhbwhcARbKqiAGwry8XuBQ-3PaX19yvyQRg0-=mo",
			"date": "2023-01-16T16:52:02.915Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=a2a38169-6784-4f42-8933-cc78c10bee2c",
			"title": null,
			"text": "I love this game it's the best I love the horror it's not that bad of a game just telling you play It pls...",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_intense",
					"rating": 2
				},
				{
					"criteria": "vaf_games_genre_action",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_car",
					"rating": 2
				}
			]
		},
		{
			"id": "461a6f36-dc90-4546-b101-f3996c508597",
			"userName": "Amr Yehiya",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6mdhbT3zTsoGU02xCCDH7Mdob1xez8sForLA-w=mo",
			"date": "2023-01-16T16:36:01.209Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=461a6f36-dc90-4546-b101-f3996c508597",
			"title": null,
			"text": "Why I have to pay 15$ for act 2 and 3 change it tiny build",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_room_escape",
					"rating": 1
				},
				{
					"criteria": "vaf_games_complex",
					"rating": 3
				}
			]
		},
		{
			"id": "671790c7-625f-4243-b8c9-3333618ced7e",
			"userName": "PINKY ROY",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6KfUUeNXz5yDwXYSuIeiHwR6RYEfb8CVfOsnRM=mo",
			"date": "2023-01-16T16:24:06.825Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=671790c7-625f-4243-b8c9-3333618ced7e",
			"title": null,
			"text": "This is so good !!! Game but ... The controlling si to hard",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "0e30be51-ffe9-49d1-bf9a-172f9c4844db",
			"userName": "M Wiggins",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6LbQRaN4TgKPxZvz63oZTRtywA1WLVl1Ch1OVy=mo",
			"date": "2023-01-16T16:22:25.839Z",
			"score": 2,
			"scoreText": "2",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=0e30be51-ffe9-49d1-bf9a-172f9c4844db",
			"title": null,
			"text": "It's a fun game but it to up all of of my space and it never saves your progress",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ecaacc50-263f-420a-a4c5-22beb9138f8d",
			"userName": "Shamim Dasurkar",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7qXMjBE4UzsLlm08paTgt1sucPVF64S4jdDxDs=mo",
			"date": "2023-01-16T15:46:41.667Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ecaacc50-263f-420a-a4c5-22beb9138f8d",
			"title": null,
			"text": "5000;60000000 point hello neighbor ₹🤑🤑🤑 30000009223₹",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_puzzle",
					"rating": 1
				},
				{
					"criteria": "vaf_games_realistic",
					"rating": 1
				},
				{
					"criteria": "vaf_games_smooth",
					"rating": 1
				}
			]
		},
		{
			"id": "026b1385-ee7a-4ff7-8147-1b4f166058fa",
			"userName": "Harkaranvir Singh",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCm0Ho_4It6-73p1oWdJ9hLroVA2ztt2sSjhS5E2",
			"date": "2023-01-16T14:46:35.305Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=026b1385-ee7a-4ff7-8147-1b4f166058fa",
			"title": null,
			"text": "Best",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "f6dd383c-56a9-4a88-872b-2ce46cdaf7aa",
			"userName": "Joshua Gore",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7zT__p1o2kzGLg7jZ9OVFFm0cCSg44Usfu4OAV=mo",
			"date": "2023-01-16T13:53:05.452Z",
			"score": 2,
			"scoreText": "2",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=f6dd383c-56a9-4a88-872b-2ce46cdaf7aa",
			"title": null,
			"text": "beat act 1 but it costs $14.99 to play act 2 and act 3, ridiculous and language keeps going back to russian",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "b9d44fa8-e262-45a6-88cd-a8c9ccf1b449",
			"userName": "Arshi Sarfaraz",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5tuG9GeWxUxW2uLce6bOkuqjm-fLywmm1KkSy5=mo",
			"date": "2023-01-16T12:32:27.911Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=b9d44fa8-e262-45a6-88cd-a8c9ccf1b449",
			"title": null,
			"text": "This is very very best game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "6ad63a7f-c1d1-41f1-b48e-34589752b695",
			"userName": "Anita Kumari",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCmdd1dZm4I6hg_WkRdYoRPU7my7RT3dMGV9tiySEw",
			"date": "2023-01-16T11:52:14.690Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=6ad63a7f-c1d1-41f1-b48e-34589752b695",
			"title": null,
			"text": "Good game my duty",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_room_escape",
					"rating": 1
				},
				{
					"criteria": "vaf_games_interactive",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_parking_simulation",
					"rating": 3
				}
			]
		},
		{
			"id": "d188271a-871b-49c8-a67b-a4cc0d66485e",
			"userName": "Ayushman Rathore",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClPWO9s4gRMDEnXS9fIheGIz0SQyNWrnzAXWwwR",
			"date": "2023-01-16T11:30:09.504Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=d188271a-871b-49c8-a67b-a4cc0d66485e",
			"title": null,
			"text": "Very nalla🖕 app Sara net kha gya phir bhi nhi chala",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "508104a3-3a53-4673-895c-9efbcc13ed7d",
			"userName": "Brian Leonard",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCmJXfwEZg93iCb3vAURnaJq4cDsicIiebz3l_YL",
			"date": "2023-01-16T08:05:33.171Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=508104a3-3a53-4673-895c-9efbcc13ed7d",
			"title": null,
			"text": "BEST GAME EVER!!!!",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_real_time_tactics",
					"rating": 3
				},
				{
					"criteria": "vaf_games_subject_space_simulation",
					"rating": 2
				},
				{
					"criteria": "vaf_games_connectivity_required_before_first_use",
					"rating": 2
				}
			]
		},
		{
			"id": "2aefa90a-72d5-4090-99eb-16c182b2818c",
			"userName": "Rabia Aqab",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4UwmYs6dL4XjNOZeyToaCNq2l_vplontVXXbro=mo",
			"date": "2023-01-16T08:00:47.728Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=2aefa90a-72d5-4090-99eb-16c182b2818c",
			"title": null,
			"text": "Ilike that game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "1bbdb196-b784-48d1-a4a2-eef4533db750",
			"userName": "Chandra Kant Upadhyay",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCm5XxYpscsNIqljH26nClj5Qm_Z6qiCR5WqH6As",
			"date": "2023-01-16T07:39:45.991Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=1bbdb196-b784-48d1-a4a2-eef4533db750",
			"title": null,
			"text": "The fabulous game ever seen",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "2d6fbb55-a399-4f21-9065-acd6d951efeb",
			"userName": "EFTE.KHAR. Hossain",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp44e8XPGlqEIl6oyghWUDO9ljVcM17QkPwHlHe7=mo",
			"date": "2023-01-16T07:01:12.490Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=2d6fbb55-a399-4f21-9065-acd6d951efeb",
			"title": null,
			"text": "It’s best",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "e1d7b014-c51c-4156-aff7-d17d20e1b343",
			"userName": "Akshay sharma",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClv2HnAuGEM1zSagRkiRKg_jqT1y7kkvNnitcsG",
			"date": "2023-01-16T05:31:57.686Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=e1d7b014-c51c-4156-aff7-d17d20e1b343",
			"title": null,
			"text": "These game is very good 😙😙",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "4d57c59d-8109-456e-af29-4551eb0480ae",
			"userName": "harith2010 12",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCluHZ49UNh2fKi8FzxzUu0DUkrRYc9KV7Wo3rOX",
			"date": "2023-01-16T05:26:06.552Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=4d57c59d-8109-456e-af29-4551eb0480ae",
			"title": null,
			"text": "I loveee it the game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "09d76d44-b834-4b77-a47f-3706599f5a88",
			"userName": "Gaming with OPTNSIDDHU",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp44nTFQvF_eAAXkQb_FfhUCcaIb0PXw-0EjELU1mg=mo",
			"date": "2023-01-16T05:18:21.200Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=09d76d44-b834-4b77-a47f-3706599f5a88",
			"title": null,
			"text": "I hate why there asking money for the full game can they just make it 🆓",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "3de2a632-e0bf-4577-be98-5c1da73b3555",
			"userName": "Daiden Roberts",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4IIWivsFAjF0xvQc7uiLLYmvuPUwK_XHp9ODsF=mo",
			"date": "2023-01-16T04:18:15.864Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=3de2a632-e0bf-4577-be98-5c1da73b3555",
			"title": null,
			"text": "it wont let me select my age",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_sokoban",
					"rating": 2
				},
				{
					"criteria": "vaf_never_display_content_language",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_skateboarding",
					"rating": 2
				}
			]
		},
		{
			"id": "f9028ec4-27c2-4df7-939e-49e8b4f570eb",
			"userName": "Flash Gordon",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7qtK6p07RinHfY5bfsKSV-CPwEhJcI90sJBJWYzw=mo",
			"date": "2023-01-16T02:43:22.884Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=f9028ec4-27c2-4df7-939e-49e8b4f570eb",
			"title": null,
			"text": "Good game add the alphas",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_action",
					"rating": 3
				},
				{
					"criteria": "vaf_games_subject_horse",
					"rating": 2
				},
				{
					"criteria": "vaf_games_single_player",
					"rating": 1
				}
			]
		},
		{
			"id": "b4efece6-83cf-477d-9bd3-e9dd5c41218c",
			"userName": "Gaming With T N G",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCktZhaa1rzGYYIW-C2YW-hqxUVdi2vYt1vp5N7gag",
			"date": "2023-01-16T01:41:50.533Z",
			"score": 3,
			"scoreText": "3",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=b4efece6-83cf-477d-9bd3-e9dd5c41218c",
			"title": null,
			"text": "we want to play secret neighbor on android devices .",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "55e27877-cb46-477b-91ea-5b1e3710d84b",
			"userName": "Kayla Pixler",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClYaPv7mMGFdc3YMWEGPL25zSqKXr7nSTUT35j3Qg",
			"date": "2023-01-16T00:31:31.325Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=55e27877-cb46-477b-91ea-5b1e3710d84b",
			"title": null,
			"text": "No don't let it is the monkey",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "1050238f-dba9-4b94-b3b7-f179dba138c9",
			"userName": "Victoria Curtis",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClzFVcWJt9LznsjQqqzGd3KaT0UWHjdv8wvCWkuMGg",
			"date": "2023-01-15T20:14:58.399Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=1050238f-dba9-4b94-b3b7-f179dba138c9",
			"title": null,
			"text": "this game is so fun i beat the game in 2days bro",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "784145b6-d1d7-46f6-ab53-566cee5e0ff2",
			"userName": "Chris Howes",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5DMy6e3fnRolvzVAkiF63bqkatwsRG4pul6rik=mo",
			"date": "2023-01-15T15:06:51.180Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=784145b6-d1d7-46f6-ab53-566cee5e0ff2",
			"title": null,
			"text": "💩",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "9087add5-d868-4eeb-b8bc-e1b68af02e8c",
			"userName": "Noah Yetter",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClf1m8WUaGhmQZkXtpuEqY_kYnt8fsr_L6ryw72",
			"date": "2023-01-15T14:41:17.112Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=9087add5-d868-4eeb-b8bc-e1b68af02e8c",
			"title": null,
			"text": "good game",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_challenging",
					"rating": 1
				},
				{
					"criteria": "vaf_games_genre_tile_matching",
					"rating": 1
				},
				{
					"criteria": "vaf_never_display_difficult_to_use",
					"rating": 2
				}
			]
		},
		{
			"id": "88c813da-cd40-4559-8c2e-c340844fd9fb",
			"userName": "Mohamed Said",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7fZAyjjfhOKTjFJhZmJ-KoOI6rJcYWDZlYq6dg=mo",
			"date": "2023-01-15T14:36:09.462Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=88c813da-cd40-4559-8c2e-c340844fd9fb",
			"title": null,
			"text": "Avery good game y'all must install it but it takes a lot of thinking and y'all might need the help from someone who played it or from youtube",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_tactical_shooter",
					"rating": 2
				},
				{
					"criteria": "vaf_games_subject_bicycle",
					"rating": 2
				},
				{
					"criteria": "vaf_games_smooth",
					"rating": 3
				}
			]
		},
		{
			"id": "852fc174-de9a-4cc2-b4c4-efed49f646b6",
			"userName": "hasibs cave",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7XwCeyEM4V5cqFCFaeB_YdAnj_yj0CG8ljgMHI=mo",
			"date": "2023-01-15T14:21:44.676Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=852fc174-de9a-4cc2-b4c4-efed49f646b6",
			"title": null,
			"text": "This game is very amezing",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_exciting",
					"rating": 1
				},
				{
					"criteria": "vaf_games_genre_action_rpg",
					"rating": 1
				}
			]
		},
		{
			"id": "1f9221bb-282f-4f85-b693-e48699a3a4e6",
			"userName": "Pro Bro",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCnXaZ-Vrdd0oD0LlTpHYvzdXuVm_rdkV1xdEb9D",
			"date": "2023-01-15T13:42:25.966Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=1f9221bb-282f-4f85-b693-e48699a3a4e6",
			"title": null,
			"text": "Very good game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "a577b2a0-6990-4226-8739-e83d531d97bd",
			"userName": "Poonam Tiwari",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6-rzDeDHvstHq__HDVhZOwnlD0pTOGMK3cUq0S=mo",
			"date": "2023-01-15T12:37:23.188Z",
			"score": 3,
			"scoreText": "3",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=a577b2a0-6990-4226-8739-e83d531d97bd",
			"title": null,
			"text": "This game is very nice but 2 part we will not playing in mobile",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ebd5d2d5-e951-44f5-82dc-89d959aaa2cf",
			"userName": "Louise Downing",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6HDpJm4qXG2Jad2iE4lM5GkBY6A8QdNHkNfRCl=mo",
			"date": "2023-01-15T11:45:48.404Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ebd5d2d5-e951-44f5-82dc-89d959aaa2cf",
			"title": null,
			"text": "I love it",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_isometric_platform",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_vehicle_simulation",
					"rating": 1
				},
				{
					"criteria": "vaf_games_entertaining",
					"rating": 1
				}
			]
		},
		{
			"id": "72dd447a-2328-4377-b67d-053eb5fd5efd",
			"userName": "Anup Guchait",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCnMqMMmWbNwSIxePaw79-IFJ99BTj0weXQaEeBD",
			"date": "2023-01-15T11:10:25.300Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=72dd447a-2328-4377-b67d-053eb5fd5efd",
			"title": null,
			"text": "This. Is. Good. Game. U. Allso. Try👇💮",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "b3b19b38-86cb-477b-8ef5-305dc3253943",
			"userName": "Danna Jezrian Barreto",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCnW8JGpd2zN2Md_8MZtrpBmSn7B-GwGBDc1W-JF",
			"date": "2023-01-15T10:47:11.443Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=b3b19b38-86cb-477b-8ef5-305dc3253943",
			"title": null,
			"text": "It's OK I guess just a bit glitchy",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "bdb774e1-7995-40e4-9788-8efee5d39e65",
			"userName": "ak__ coder",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCn3ed77xIi98VejQdJejbVwYha0Wq7FPG5PHHhNWA",
			"date": "2023-01-15T10:40:13.163Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=bdb774e1-7995-40e4-9788-8efee5d39e65",
			"title": null,
			"text": "Osm",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "6ffe1d39-91af-47af-afab-b4caed1fb307",
			"userName": "shyam sunder Mishra",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClKRxVNj-C_YfVBMRcaP1PJAZzJ1V2uiFI6WPhi",
			"date": "2023-01-15T10:23:39.267Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=6ffe1d39-91af-47af-afab-b4caed1fb307",
			"title": null,
			"text": "Pls do everything free but its so cool",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "1640c473-e76a-4799-9766-af2c51fa59f8",
			"userName": "ST Quality Collection",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCn9TunuuKORvgwY0xEGjs1yBs1M3ah9YlXSN_Qd",
			"date": "2023-01-15T09:05:12.243Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=1640c473-e76a-4799-9766-af2c51fa59f8",
			"title": null,
			"text": "I HATE THIS GAME SO MUCHHH BUT STILL was GOOD BUT SO MANYYYYYY BUGS LIKE IN ACT 3 WHERE YOU HAVE TO JUMP THROUGH THAT WINDOW TYPE THING IT MAKES ME STUCK I HATE IT IF YOU FIX ALL BUGS THEN ILL RATE IT 5 STARS (EVEN THOUGH IHAVE 200 OR SOMETHING DOLLAR PURCHASE! POOR SERVICE)",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "23c2c873-3bea-4cc4-8119-c36fc2ad8003",
			"userName": "Hari Lal",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4aBiFOQtWrBl3b_yobTd35bqy8xysIa9F1Bw55=mo",
			"date": "2023-01-15T08:58:18.810Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=23c2c873-3bea-4cc4-8119-c36fc2ad8003",
			"title": null,
			"text": "गुड",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_never_display_easy_to_use",
					"rating": 1
				},
				{
					"criteria": "vaf_games_multi_player_v2",
					"rating": 1
				},
				{
					"criteria": "vaf_games_genre_third_person_shooter",
					"rating": 1
				}
			]
		},
		{
			"id": "71f935c3-55c4-4ba3-81a1-6dec0bbbda85",
			"userName": "Music Lyrics",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5EBwgm_g6RnKNBKrLqyD_Y8cw0KsPo6Wp5yM6x=mo",
			"date": "2023-01-15T08:57:50.824Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=71f935c3-55c4-4ba3-81a1-6dec0bbbda85",
			"title": null,
			"text": "It's is so Good app i m lucky to Accept this App ☺️ love is EGO and we always love And respect Each other to ego will be Hundred % Right",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "7f89cc1d-ebad-4862-a6cc-43b003db46be",
			"userName": "Ben Sole",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7jOGsl9sL-PeKNUCgwD08daF1HJLLlDHkTYgms=mo",
			"date": "2023-01-15T08:52:55.600Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=7f89cc1d-ebad-4862-a6cc-43b003db46be",
			"title": null,
			"text": "Really good, the ads can be annoying but i just turned of my internet and problem solved, the AI is pretty bad but he's also dumb.",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "5a098ddc-7aff-46c1-8946-694b04435af9",
			"userName": "Eishaan Haider",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClYGizrkUrlzXCOJW050ME_ziWQuCdK5QZRBvPh6yw",
			"date": "2023-01-15T08:46:59.585Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=5a098ddc-7aff-46c1-8946-694b04435af9",
			"title": null,
			"text": "Good game but it is have so many glitches but the graphics is so fantastic ♥️",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "e071a244-ffdb-410b-aa35-056511c31478",
			"userName": "Ayyub Davids",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4or9EQjVE_YMTaVD_45XAD8zhqQh2SpJQRkE7g=mo",
			"date": "2023-01-15T08:40:12.382Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=e071a244-ffdb-410b-aa35-056511c31478",
			"title": null,
			"text": "It,s cool for me very actually I like horror games",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "cdee77c3-4704-4639-91b6-3bba8264c9d2",
			"userName": "fozia Azam",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7pAEoAEY-PBhG6FCFkPSBpUok4TKCmkDkGphLU=mo",
			"date": "2023-01-15T08:30:03.495Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=cdee77c3-4704-4639-91b6-3bba8264c9d2",
			"title": null,
			"text": "Make this home bigger Like shiva and kanzo please 🙏🙏🤲",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ab600f2c-ad14-4126-bb6b-8396ee22d7d1",
			"userName": "PRAFULL JHALA",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5hp1f9L6pvb72_cHOZ_FBH7UbyyWDc5lysFoh0=mo",
			"date": "2023-01-15T08:06:16.255Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ab600f2c-ad14-4126-bb6b-8396ee22d7d1",
			"title": null,
			"text": "Execellent",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "2993af77-52e2-4a6a-89f7-1ce4971aa45f",
			"userName": "Dipak Sisodiya",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6mYyoZJqTObma2-_c1bbpJuELl4dQkQ5Bzla9v=mo",
			"date": "2023-01-15T08:02:03.181Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=2993af77-52e2-4a6a-89f7-1ce4971aa45f",
			"title": null,
			"text": "This is so amazing",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "0037b2e4-26e9-47b3-a8c6-31f92a275275",
			"userName": "Jagadees Varan",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7cr-TwqqZqtQsC5XKFfXqIMwPvp6ulHhQPUm3W=mo",
			"date": "2023-01-15T07:33:03.642Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=0037b2e4-26e9-47b3-a8c6-31f92a275275",
			"title": null,
			"text": "Jeeva .j",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "6aa03eb5-e8df-4ecf-8314-e5567f87cf9a",
			"userName": "norovbadam tamir",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCnl4h0NGMAgFcRlNMbMvyhXmFhIKnuz8Mjub_jZMw",
			"date": "2023-01-15T07:18:07.243Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=6aa03eb5-e8df-4ecf-8314-e5567f87cf9a",
			"title": null,
			"text": "Puerto gahal ygus malade uh vushida momob Barta guiza",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "d87d63ef-a555-455b-84d5-0aa7aa06f0c3",
			"userName": "Super CG",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp43GH1e9aLZViMBB9FRBRx2zRxMC77t9_CJgi-d=mo",
			"date": "2023-01-15T05:30:10.464Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=d87d63ef-a555-455b-84d5-0aa7aa06f0c3",
			"title": null,
			"text": "Awesome game and the best game among all of the horror games!",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_entertaining",
					"rating": 1
				}
			]
		},
		{
			"id": "e3732cbc-78c3-490e-88f6-9309b5c50a04",
			"userName": "NIKHIL DAS",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCmvv00oDo1xHPu6Ao6SjDL3a8K1xxoEgfL2OUIwnA",
			"date": "2023-01-15T04:28:05.349Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=e3732cbc-78c3-490e-88f6-9309b5c50a04",
			"title": null,
			"text": "Advik Nikhil UKG D and I have to wait for the 5 to be 5th March as 59 59 is away and ruu5 has not been able and has been a long day and has been",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_subject_parking_simulation",
					"rating": 2
				},
				{
					"criteria": "vaf_games_genre_third_person_action_adventure",
					"rating": 1
				},
				{
					"criteria": "vaf_games_challenging",
					"rating": 1
				}
			]
		},
		{
			"id": "87dad8af-eaf7-4983-abed-1ccc0977497b",
			"userName": "Gail Winn",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp79IFeU2nXEONkB-RrisW5K7RWfDYh5bSBa1z_g=mo",
			"date": "2023-01-15T04:13:38.992Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=87dad8af-eaf7-4983-abed-1ccc0977497b",
			"title": null,
			"text": "Y e s A w s o m e d o w n l o a d I t Ŋ⁰‽Ẅ—¿<@>",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "f6b5167a-3e16-40b7-b68e-5c2868eba24a",
			"userName": "Pramod",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCk9g9U5CDNGkWh0Uv1QvjLaoFJ909gNRcTbmwmlCpA",
			"date": "2023-01-15T02:31:08.612Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=f6b5167a-3e16-40b7-b68e-5c2868eba24a",
			"title": null,
			"text": "Very good game and i like very much and intresting",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "1042dcad-a2ad-4088-8a0f-a9a731da4953",
			"userName": "donterrius king",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7bCqQWKy6tPzGLfeVTk22amWM5Cj6F9rZ_7Igc=mo",
			"date": "2023-01-15T01:17:37.771Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=1042dcad-a2ad-4088-8a0f-a9a731da4953",
			"title": null,
			"text": "i like it its cool my son like it but lowkey it makes me jumps when the dude come out",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_memory",
					"rating": 1
				},
				{
					"criteria": "vaf_never_display_easy_to_use",
					"rating": 1
				},
				{
					"criteria": "vaf_games_multi_player_v2",
					"rating": 3
				}
			]
		},
		{
			"id": "df15c9e8-0401-4bbd-8fc5-28dcde163e92",
			"userName": "Princess Prince",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCnyEA_vTuO04wOfWQYlUMGMOQtHVjJwHEI8XWsV",
			"date": "2023-01-15T01:08:35.701Z",
			"score": 3,
			"scoreText": "3",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=df15c9e8-0401-4bbd-8fc5-28dcde163e92",
			"title": null,
			"text": "Edit : bugs... LOTS OF LOTS OF bugs lemme explain, so basically when I was in mart's basement (hello neighbor) I was in there then my screen froze, THEN another time when I was gonna play so you click on the app blahh blah blah blah blah I was on the waiting screen and I'VE BEEN THERE FOR HOURS Y'ALL HEAR ME? HOURS (1-3hours) so yeah that's- oh wait one more, when I was playing you know the tutorial and everything yeah so, when it was explaining the jump button it was a different language so bye",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "5e601d58-b5fb-42cc-a2db-34d82ecb16b5",
			"userName": "Irene Serene",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6YzNlvCPr94sBmP53kqMJ8SzBEI0ZbwL7f6Xii=mo",
			"date": "2023-01-15T00:31:03.387Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=5e601d58-b5fb-42cc-a2db-34d82ecb16b5",
			"title": null,
			"text": "This game 🎮 is so good i play this before when i was younger",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "c9a34a29-680e-4ccc-bd65-67385aacc5e3",
			"userName": "Juzten Ebert",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCk5NgFtjhQr_whSLsWi2r8aXQN0_3kF0ooH5ZyNbQ",
			"date": "2023-01-14T23:59:11.739Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=c9a34a29-680e-4ccc-bd65-67385aacc5e3",
			"title": null,
			"text": "Cant even go back to alpha 1 like in thr screen shots",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_shoot_em_up",
					"rating": 2
				},
				{
					"criteria": "vaf_games_subject_motorcycle",
					"rating": 2
				},
				{
					"criteria": "vaf_games_cute",
					"rating": 2
				}
			]
		},
		{
			"id": "54539c51-d356-4ac2-b777-c8b121da3af0",
			"userName": "Beverly Wright",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4GdhqskSIlKhdi5PKdtW70acSwmMD8HmnJID6v=mo",
			"date": "2023-01-14T22:41:39.217Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=54539c51-d356-4ac2-b777-c8b121da3af0",
			"title": null,
			"text": "I know you just moved in but what were you thinking trying to get trying to get trying to get get you gone",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "9842a0ea-7625-4ff8-a05f-8e0107f6cc8a",
			"userName": "A Google user",
			"userImage": "https://play-lh.googleusercontent.com/EGemoI2NTXmTsBVtJqk8jxF9rh8ApRWfsIMQSt2uE4OcpQqbFu7f7NbTK05lx80nuSijCz7sc3a277R67g",
			"date": "2023-01-14T21:40:09.900Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=9842a0ea-7625-4ff8-a05f-8e0107f6cc8a",
			"title": null,
			"text": "i cant use it on chromebook becaues it woan't respond to my cliks i tried my trackpad,my mouse and controler still nothing",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_minigames",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_parking_simulation",
					"rating": 2
				},
				{
					"criteria": "vaf_never_display_negative_ads_impact",
					"rating": 2
				}
			]
		},
		{
			"id": "f933f5f2-e46b-46c4-aace-a16787e727b7",
			"userName": "Mohan Singh",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp49tYDFnwLi23e5AolXp4fSvcZXE59015nLoX9O=mo",
			"date": "2023-01-14T20:40:59.194Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=f933f5f2-e46b-46c4-aace-a16787e727b7",
			"title": null,
			"text": "XD",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "d27eef08-ddd3-4fbf-9b4e-05c6fa6a2693",
			"userName": "Derek Geyer",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7B62709DWXYvZhtcU3fxhJ6_BYjMMZihJSXZCG=mo",
			"date": "2023-01-14T18:27:48.103Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=d27eef08-ddd3-4fbf-9b4e-05c6fa6a2693",
			"title": null,
			"text": "This game is a mystery",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_mystery_puzzle",
					"rating": 2
				},
				{
					"criteria": "vaf_games_multi_player_friends",
					"rating": 2
				},
				{
					"criteria": "vaf_games_subject_parking_simulation",
					"rating": 2
				}
			]
		},
		{
			"id": "c993314c-cab3-469f-a907-3630ac20b467",
			"userName": "Hasnain Khatri",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7JiSRvjm0FZZlYAF7kl378Q_gdy6Oo8V-WzAzW=mo",
			"date": "2023-01-14T18:09:16.520Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=c993314c-cab3-469f-a907-3630ac20b467",
			"title": null,
			"text": "DOWNLOADING IS SO SLOW VERY BAD😠",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "2f66ae42-2e73-45db-b635-7b4289851550",
			"userName": "David Newcomb",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCnzS2llDbPtXLh0IcfboM3MY9gyUouVNrhCKwGDKw",
			"date": "2023-01-14T17:38:51.849Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=2f66ae42-2e73-45db-b635-7b4289851550",
			"title": null,
			"text": "You should change the start",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ae536667-15c9-4d04-ba26-884d844d1936",
			"userName": "VX Tanwar",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCl-Z0BbFvSvpwLANBylc_WBOc2TNeWWite__al9IQ",
			"date": "2023-01-14T17:34:02.770Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ae536667-15c9-4d04-ba26-884d844d1936",
			"title": null,
			"text": "The loading screen says that \" u didn't purchased this game \" do something!!",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "cf37d8e6-a231-41d0-ae70-f91f7b6b19e1",
			"userName": "itzayana Morales",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7EXZFMeFVURpfngaPkFTAPNw7VRsp8hmt1HAlP=mo",
			"date": "2023-01-14T16:57:41.470Z",
			"score": 2,
			"scoreText": "2",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=cf37d8e6-a231-41d0-ae70-f91f7b6b19e1",
			"title": null,
			"text": "it had a bug in the loding screen when i had to put in how old am i",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "d094f5ce-438a-4703-a0f4-2a9180854269",
			"userName": "My name is None of you’re business",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCkh8qgrA2-AJjboPYlf6Y21x-WBKwE4GrRVhrmZ",
			"date": "2023-01-14T16:27:04.677Z",
			"score": 2,
			"scoreText": "2",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=d094f5ce-438a-4703-a0f4-2a9180854269",
			"title": null,
			"text": "This game was good but now it's literally just ruined hello neighbor alpha was good and this could've been scary and it had potential that's why I gave it 2 stars but the game is rushed it's messy and laggy there really isn't a point act 3 and 4 cause it literally spoils everything in act 1 and some puzzles generally make my brain hurt I hate this game. Im sorry the whole game is awful and each update it gets worse",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ebf68767-6b27-49b1-8542-da09ca733b28",
			"userName": "Michael Thompson",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5EjYKN7yG085IxqCcn3HPEDF_SWwuLhmcfhew4=mo",
			"date": "2023-01-14T15:38:51.368Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ebf68767-6b27-49b1-8542-da09ca733b28",
			"title": null,
			"text": "yay .",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_jigsaw",
					"rating": 2
				},
				{
					"criteria": "vaf_games_relaxing",
					"rating": 2
				},
				{
					"criteria": "vaf_games_subject_parking_simulation",
					"rating": 2
				}
			]
		},
		{
			"id": "8d939590-0250-4300-a51f-505d1e2d3514",
			"userName": "Surendra Kumar",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6BVPu4PF162MTtPb5yQwZjIuU4MBLlDcbhT1eC=mo",
			"date": "2023-01-14T15:32:47.949Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=8d939590-0250-4300-a51f-505d1e2d3514",
			"title": null,
			"text": "Very bad",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_physics_based_puzzle",
					"rating": 3
				},
				{
					"criteria": "vaf_games_subject_skateboarding",
					"rating": 2
				}
			]
		},
		{
			"id": "703c492a-6b40-4ab5-953e-5bb301075395",
			"userName": "Leesie",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7PxjnASPtLRqoOIhvb3W6ms7BFRp32tGbuPcYe=mo",
			"date": "2023-01-14T14:37:55.470Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=703c492a-6b40-4ab5-953e-5bb301075395",
			"title": null,
			"text": "i have been wanting to play this game so much but it went to the age and did not let me play so can you fix this",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "33198797-78b3-425c-b1ad-8ece64b034b3",
			"userName": "raneth raveesha",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5ivwl4s_hJ3oLfSXitQXGE2e7abG0nfXVIUFVR=mo",
			"date": "2023-01-14T13:25:10.948Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=33198797-78b3-425c-b1ad-8ece64b034b3",
			"title": null,
			"text": "It is so cool we nide2",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "4b135691-c6b1-45d2-9e59-112f1089d35a",
			"userName": "Nejc",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4Re41hBNjdh_SeDIhtMo3NeUc-iJaCadTz1CgV=mo",
			"date": "2023-01-14T12:51:31.810Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=4b135691-c6b1-45d2-9e59-112f1089d35a",
			"title": null,
			"text": "A+",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_massively_multiplayer_online",
					"rating": 2
				},
				{
					"criteria": "vaf_games_multi_player_v2",
					"rating": 2
				},
				{
					"criteria": "vaf_games_subject_parking_simulation",
					"rating": 2
				}
			]
		},
		{
			"id": "b2b82600-eb89-45a4-a094-d95cede4d83f",
			"userName": "3yal m7md",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4ECeKGg9DZsbVwfXtuGXQAr6-_8bGqaBtAYtHN=mo",
			"date": "2023-01-14T12:24:13.908Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=b2b82600-eb89-45a4-a094-d95cede4d83f",
			"title": null,
			"text": "Wow❤️",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "2e03ce5a-874c-4d2a-87bc-b39199effdb8",
			"userName": "Yolanda Abarquez",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5YlwDZokmEDP2vh2BuWF6U-9FzGIY0E5vUl1wz=mo",
			"date": "2023-01-14T10:53:40.190Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=2e03ce5a-874c-4d2a-87bc-b39199effdb8",
			"title": null,
			"text": "HelloNeighbor Act 1 Nicky's Diaries",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_subject_farm",
					"rating": 2
				}
			]
		},
		{
			"id": "1b5291cf-a803-42df-b311-4d4dac0cc15f",
			"userName": "Dhani Adi Syaputra",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCnY5kRvk2sY-vmaE8jgdyk4H6w-fNhlqD0bUal14A",
			"date": "2023-01-14T08:50:16.893Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=1b5291cf-a803-42df-b311-4d4dac0cc15f",
			"title": null,
			"text": "Belom nyobain tapi 1gb jadi nya full bintang",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_motor_sports",
					"rating": 3
				},
				{
					"criteria": "vaf_games_massively_multi_player",
					"rating": 2
				},
				{
					"criteria": "vaf_games_subject_flight",
					"rating": 1
				}
			]
		},
		{
			"id": "1f7b9aec-5967-41e6-b591-e0bfd490df50",
			"userName": "Shafiq ch",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5BChbaE42gfJQ5efi7iMIJjRitaUbCJFtPn6dy=mo",
			"date": "2023-01-14T08:39:04.432Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=1f7b9aec-5967-41e6-b591-e0bfd490df50",
			"title": null,
			"text": "This game is so interesting game iam so likely I play this game 🎮 😇🥰",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_first_person_shooter",
					"rating": 1
				}
			]
		},
		{
			"id": "e2545a0d-3816-4d82-98aa-586fa3932f42",
			"userName": "Emma Larson",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7XFzJagSqtKgCYLF49ma-372Dl1SElI9B30g-1=mo",
			"date": "2023-01-14T08:30:42.407Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=e2545a0d-3816-4d82-98aa-586fa3932f42",
			"title": null,
			"text": "🐺🐺🐺🐺🐺🐺🐒🐵🐵🐵🐁",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "2bf27f80-6265-46d4-9665-79b5fc210f4f",
			"userName": "fun with Aabiya",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp69IwkW7Lci9KHdP_ejRDRA-Aww8e80nDbiRwqGNw=mo",
			"date": "2023-01-14T07:29:28.584Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=2bf27f80-6265-46d4-9665-79b5fc210f4f",
			"title": null,
			"text": "I really love the game but the police and chef throwing me out",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "db250c5a-8ca5-4d92-bce9-503db64160f6",
			"userName": "haridas Das",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6hVJm_5Tx2B-VCBnwefdI89miwJ0xc9XmbB_6c=mo",
			"date": "2023-01-14T05:03:56.809Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=db250c5a-8ca5-4d92-bce9-503db64160f6",
			"title": null,
			"text": "Thish is the best game foravere",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "03435515-3be1-434a-b4aa-ffd18fc09dad",
			"userName": "Aarav Kumar",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7Bj1otGDx0TToOSKlD2pg6DZj2AM8nRtGpYWGh=mo",
			"date": "2023-01-14T04:08:18.159Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=03435515-3be1-434a-b4aa-ffd18fc09dad",
			"title": null,
			"text": "This game is outstanding the graphics is very good but one problem for me plss this boy characters make handsom",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ed290ba9-bae4-4338-8fe0-66edc859be93",
			"userName": "McKinley Woodard",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClplJu5NVmHrxi_3S-jxZeWqV3J_Anvcpu_AuOL",
			"date": "2023-01-14T02:51:42.622Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ed290ba9-bae4-4338-8fe0-66edc859be93",
			"title": null,
			"text": "it's really cool i finshed the game it's good qalltay",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "d222e013-65c6-4f50-805c-c199d86ee8b4",
			"userName": "RANL 2",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp58HJxK1wJtyuvLSIaNlRCL2n2nLt5zTLgNv_oy=mo",
			"date": "2023-01-14T01:42:59.642Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=d222e013-65c6-4f50-805c-c199d86ee8b4",
			"title": null,
			"text": "So good neighbor is amazing",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "3eacca0b-47c5-4a9d-b988-74bd83e1c906",
			"userName": "Jovan Balls",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5wND2U8INxTzbV_aOBh2o8lkkEIh2sGRO1nbTb=mo",
			"date": "2023-01-14T01:08:48.148Z",
			"score": 3,
			"scoreText": "3",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=3eacca0b-47c5-4a9d-b988-74bd83e1c906",
			"title": null,
			"text": "Okay so, I installed the game everything is going well and out of nowhere it puts some text saying \"load failed because you may not have purchased this game\" I played it before and everything was ok please can you help me out?",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "dbb30bf5-cf76-48ce-be7c-3ee4165eb3bf",
			"userName": "A Google user",
			"userImage": "https://play-lh.googleusercontent.com/EGemoI2NTXmTsBVtJqk8jxF9rh8ApRWfsIMQSt2uE4OcpQqbFu7f7NbTK05lx80nuSijCz7sc3a277R67g",
			"date": "2023-01-14T00:52:28.481Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=dbb30bf5-cf76-48ce-be7c-3ee4165eb3bf",
			"title": null,
			"text": "Good",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_subject_animal",
					"rating": 2
				}
			]
		},
		{
			"id": "414828ae-a14e-445a-b65b-2e3da8582927",
			"userName": "Jacob Argaon",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7HlqTuJHk5mpg2znfNwJUikdSGfVjpc3uaKp75=mo",
			"date": "2023-01-13T22:49:24.587Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=414828ae-a14e-445a-b65b-2e3da8582927",
			"title": null,
			"text": "is so gay",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "3e54de2c-0f2d-4a45-99ac-81fba2842a05",
			"userName": "Samantha Wallace",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCl9C7zipgAhW5zXODMow2R0ppwbyMDd_j3_A1Dz2A",
			"date": "2023-01-13T21:41:45.658Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=3e54de2c-0f2d-4a45-99ac-81fba2842a05",
			"title": null,
			"text": "it ask for my age but i cant do nothing like why",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_complex",
					"rating": 1
				},
				{
					"criteria": "vaf_games_genre_adventure",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_domino",
					"rating": 1
				}
			]
		},
		{
			"id": "26fae09f-4d38-4ab1-a036-ab7f4a993bf8",
			"userName": "LAMIA games",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCkSH-aR_4Cpn4ooTPrRFGWODBMkuZF02QfMoSvM3w",
			"date": "2023-01-13T21:24:19.586Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=26fae09f-4d38-4ab1-a036-ab7f4a993bf8",
			"title": null,
			"text": "I love it",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "b1a03e19-50fe-468d-9c00-8f7728b0dcdd",
			"userName": "Luke Futch",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5KKcXnOfyOOGWkm9sI6vGaoskUSChBxdoGXWnk=mo",
			"date": "2023-01-13T21:10:11.646Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=b1a03e19-50fe-468d-9c00-8f7728b0dcdd",
			"title": null,
			"text": "I just want to say something to tiny build this game is so fun if you can make the next level pls try to make all the levels free where you don't have to buy it thank you",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 1,
			"criterias": []
		},
		{
			"id": "c539edbf-8c82-4ebd-9879-80c71208f0f2",
			"userName": "porsha and Ray silmon",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WClixURqQD8YqcJyLUkAs2UrVdr8zdMx4d6Tp4PI9A",
			"date": "2023-01-13T18:37:08.434Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=c539edbf-8c82-4ebd-9879-80c71208f0f2",
			"title": null,
			"text": "Is so... ez Like I he is sad at the sad part",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "70f441ad-45f7-4fa4-9772-bdcd674b214e",
			"userName": "Ayansh Shreya",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4f41Fy5y_8dqTMynhxnZsGeRomo0zQ7Bme5qyK=mo",
			"date": "2023-01-13T14:38:53.254Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=70f441ad-45f7-4fa4-9772-bdcd674b214e",
			"title": null,
			"text": "This is the very nice and the good game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ced770d8-4ddf-4b60-ab9c-4d76b1712db5",
			"userName": "Hadi Hassan",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7NBAXzWCkT9Dsg-oipFlKHxBBTBdNOfWJ2Kc6y=mo",
			"date": "2023-01-13T13:00:14.580Z",
			"score": 3,
			"scoreText": "3",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ced770d8-4ddf-4b60-ab9c-4d76b1712db5",
			"title": null,
			"text": "It's good game but annoying thing is I can't through properly the freezes multiple times and no chance to do anything I have to restart ,(To me)...... if the all problems got fixed so immediately it's the best game and I recommend\"choo choo Charles \"to play as a horror game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 4,
			"criterias": []
		},
		{
			"id": "a1647a2c-2381-4fb7-a582-e998ab169bae",
			"userName": "Mohammad Samnan",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCl3mgTx7s0ECh7Ca8fgKtqaucO51FnPUJzslxKW",
			"date": "2023-01-13T12:59:44.489Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=a1647a2c-2381-4fb7-a582-e998ab169bae",
			"title": null,
			"text": "Best",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "7d0ab748-47de-409e-a450-8611452e834f",
			"userName": "alok singh",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7jWdWn8Kg-jDLPOjqHeqh_tIKrnm6sKUjOEbru=mo",
			"date": "2023-01-13T11:16:15.768Z",
			"score": 2,
			"scoreText": "2",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=7d0ab748-47de-409e-a450-8611452e834f",
			"title": null,
			"text": "This Game is very poor because It Los my phone network. So i couldn't give them 5 star. .•♫•THANKS•♫•.",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "5872ff0a-192c-484d-b748-91daa95c0045",
			"userName": "Vedant Chilmulwar",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4CUi4jCNOLBL-Mvdanr5AaqwOsu0_DABhGQebM=mo",
			"date": "2023-01-13T10:47:18.273Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=5872ff0a-192c-484d-b748-91daa95c0045",
			"title": null,
			"text": "Nice game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "524bc906-f63e-482b-9ba8-66a1cdf401f3",
			"userName": "Narsi Ram",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6FYvwE0V2W8MKH9-YrBh3Tti1vgQATr0bxcIEu=mo",
			"date": "2023-01-13T10:32:53.254Z",
			"score": 3,
			"scoreText": "3",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=524bc906-f63e-482b-9ba8-66a1cdf401f3",
			"title": null,
			"text": "Where is hello neighbor 2 and alpha1. 5",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 1,
			"criterias": [
				{
					"criteria": "vaf_games_subject_farm",
					"rating": 2
				},
				{
					"criteria": "vaf_games_genre_mystery_adventure",
					"rating": 1
				},
				{
					"criteria": "vaf_games_complex",
					"rating": 3
				}
			]
		},
		{
			"id": "381f1e26-ac06-46c8-9491-036c7611d6b1",
			"userName": "Bindu Sharma",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6uZiKzliSO0vkth2amkF4frPxa0jkR1eCTUFaf=mo",
			"date": "2023-01-13T09:47:54.266Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=381f1e26-ac06-46c8-9491-036c7611d6b1",
			"title": null,
			"text": "Tatting game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "ae454e6f-5fde-4ce6-bc15-b24701c84b14",
			"userName": "Aaftab Bhatti",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp45YecF_m5K9g_NzuqEXu-INEU8grm-2er5YyAF=mo",
			"date": "2023-01-13T08:31:33.830Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=ae454e6f-5fde-4ce6-bc15-b24701c84b14",
			"title": null,
			"text": "So difikal",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "6925fadb-b486-41cb-8c81-1464aef30ce1",
			"userName": "Biju Bakshi",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4rZOA0EYyJkTiHwVHm1QGucCyHfVAkapweoKc=mo",
			"date": "2023-01-13T07:35:28.717Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=6925fadb-b486-41cb-8c81-1464aef30ce1",
			"title": null,
			"text": "Op",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_racing",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_karate",
					"rating": 1
				}
			]
		},
		{
			"id": "cd06cc4b-97c1-4a35-8d0c-d1926c0fbb8b",
			"userName": "Neetu Kumari",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp41d9eslmgTuvIYC6NJargm-cCvd-FAFbcUVzyN=mo",
			"date": "2023-01-13T07:32:05.768Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=cd06cc4b-97c1-4a35-8d0c-d1926c0fbb8b",
			"title": null,
			"text": "So good",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "d9862bce-b112-443d-a6e6-4ef663be4a2c",
			"userName": "Naman Choudhary",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp58a4u6WTgSUg8K8DQtkAfUtVGAd7W7NrxrIBZU=mo",
			"date": "2023-01-13T06:02:56.304Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=d9862bce-b112-443d-a6e6-4ef663be4a2c",
			"title": null,
			"text": "When come hello neighbour 2 on android",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "4f3e587b-e197-457d-a356-b063b48bb1d6",
			"userName": "Mamta Tiwari",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6jbEXnIV1c1OPQqLjw9Hn0FzqNqYAKqccPoHob=mo",
			"date": "2023-01-13T05:23:39.734Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=4f3e587b-e197-457d-a356-b063b48bb1d6",
			"title": null,
			"text": "Very good",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "e7af8671-71f5-4704-92ec-73e1a9ef15e5",
			"userName": "Ahmed Looth",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5KYA8hiwlj9aaNYo4JzjoyAUSavyKybuV63ozh=mo",
			"date": "2023-01-13T05:20:43.938Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=e7af8671-71f5-4704-92ec-73e1a9ef15e5",
			"title": null,
			"text": "The game is so cool.",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "2126af33-9202-4fa3-a36e-bf78e0a6d2d2",
			"userName": "Basanti Mahato",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCnVo98uostDpJuYRG9Iv04KvnPkYeVuXXlySedabXU",
			"date": "2023-01-13T04:45:33.370Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=2126af33-9202-4fa3-a36e-bf78e0a6d2d2",
			"title": null,
			"text": "A nice game ...... I love it alot..... Without internet connection......",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_sim_racing",
					"rating": 3
				},
				{
					"criteria": "vaf_games_entertaining",
					"rating": 1
				},
				{
					"criteria": "vaf_games_educational",
					"rating": 2
				}
			]
		},
		{
			"id": "9e04e4f9-32ac-4391-94d7-480315353c9d",
			"userName": "Aidan Rahaman",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7MKl9YXqbQ1ddrDOJlPJmZdsSNGhJRb0uS6CRn=mo",
			"date": "2023-01-13T01:16:50.445Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=9e04e4f9-32ac-4391-94d7-480315353c9d",
			"title": null,
			"text": "Can you make all chapters free plssss I beg you I am kid you know 🙏🙏🙏🙏🙏🙏🙏 then I will like your game and DON'T MAKE GAME BUY OK ...................................... I PROMISE",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_memory",
					"rating": 1
				},
				{
					"criteria": "vaf_games_cute",
					"rating": 1
				},
				{
					"criteria": "vaf_games_subject_drift_racing",
					"rating": 2
				}
			]
		},
		{
			"id": "5180807c-6e2c-4d85-9830-97c905b2ec01",
			"userName": "Will Cooper",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7YNpGAPSDCcR7SsOS5-sBb5PVyG4N3rkDVxS-e=mo",
			"date": "2023-01-12T23:00:02.224Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=5180807c-6e2c-4d85-9830-97c905b2ec01",
			"title": null,
			"text": "It's a fun stealth game with a lot of puzzles",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_subject_horse",
					"rating": 2
				},
				{
					"criteria": "vaf_games_educational",
					"rating": 2
				}
			]
		},
		{
			"id": "d5e53dba-fcf2-426f-9deb-0bc067029468",
			"userName": "Maddox Garrett",
			"userImage": "https://play-lh.googleusercontent.com/a-/AD5-WCnfi5nRsjP1ixZtfQINBYxj_8oAxNg7BDYFFsHAQw",
			"date": "2023-01-12T20:27:23.577Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=d5e53dba-fcf2-426f-9deb-0bc067029468",
			"title": null,
			"text": "coolities are very good but I don't like the fact that you have to pay for the rest of the game",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "610c8782-f180-4699-874f-d5e3150f8be3",
			"userName": "Parbhat Singh",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6qVFCt6hxkI2VsL3DBoschJ8pZXfkRSexEvyK7=mo",
			"date": "2023-01-12T16:26:45.834Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=610c8782-f180-4699-874f-d5e3150f8be3",
			"title": null,
			"text": "Bhen chod",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "d8a07141-94cc-4f67-b7da-0276dc422d62",
			"userName": "Nimra Umair",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4bocAzGO_HJigR82VCuBZ0slRU6RCBNoIMcCQr=mo",
			"date": "2023-01-12T14:06:14.673Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=d8a07141-94cc-4f67-b7da-0276dc422d62",
			"title": null,
			"text": "Op game for android op ,,😎",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "f86340df-df33-48be-851e-1f80e9271797",
			"userName": "Dragan Gajic",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp4W86MeFF8nlOCfzL6vVWDL7Eb4r0qJ_pQ-fwyK=mo",
			"date": "2023-01-12T13:29:12.141Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=f86340df-df33-48be-851e-1f80e9271797",
			"title": null,
			"text": "Its ok",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "610e1566-357c-4d18-86b3-fa504a4d3fe8",
			"userName": "Deema Majali",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp6UWErtCdrFGs0GFSscjkc8cCtu8nm5YJw5akgw=mo",
			"date": "2023-01-12T13:11:10.542Z",
			"score": 4,
			"scoreText": "4",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=610e1566-357c-4d18-86b3-fa504a4d3fe8",
			"title": null,
			"text": "It is a good game but I don't like the fact that you have to tap on the doors to open them and it does not save the game for me",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": [
				{
					"criteria": "vaf_games_genre_shooting",
					"rating": 2
				},
				{
					"criteria": "vaf_never_display_difficult_to_use",
					"rating": 3
				},
				{
					"criteria": "vaf_games_subject_parking_simulation",
					"rating": 2
				}
			]
		},
		{
			"id": "3f132fb6-1e53-4677-8953-17bf4f77e821",
			"userName": "Neeta Sachdev",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp5TK47UlMkHvewSRJ18uJC0XuoFfWYfQReUbRiF=mo",
			"date": "2023-01-12T13:09:58.305Z",
			"score": 1,
			"scoreText": "1",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=3f132fb6-1e53-4677-8953-17bf4f77e821",
			"title": null,
			"text": "Very bad",
			"replyDate": null,
			"replyText": null,
			"version": null,
			"thumbsUp": 0,
			"criterias": []
		},
		{
			"id": "485853e8-cb03-4c97-9266-f97dc8623559",
			"userName": "Thiagarajan Mani",
			"userImage": "https://play-lh.googleusercontent.com/a/AEdFTp7UuOI0UKtJZ2RVk_BmQ-6BySNF2bkiUEZqIrh_=mo",
			"date": "2023-01-12T11:50:40.176Z",
			"score": 5,
			"scoreText": "5",
			"url": "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&reviewId=485853e8-cb03-4c97-9266-f97dc8623559",
			"title": null,
			"text": "i like this game is nice at all thank you mr peterson 😃😊😀😄😁😆😃😊😀😄😁",
			"replyDate": null,
			"replyText": null,
			"version": "1.0",
			"thumbsUp": 0,
			"criterias": []
		}
	]
}
```

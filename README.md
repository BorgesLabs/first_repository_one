require 'jumpstart_auth'

class MicroBlogger
	def initialize
		puts "TwitterBot, activated"
		@client = JumpstartAuth.twitter
	end

	def tweet (post) 
		if post.length < 140
			@client.update(post)
		else
			puts "sorry, message limit is 140."
		end
	end

	def followers
	 	x = @client.followers 
	 	x.each do |follower|
	 		z = []
	 		puts follower[:user_name]
	 		z << follower[:user_name]
	 		puts z
	 	end
	end

	def dm(user_name, message)
		tweet("d #{user_name} #{message}")

	end

	def spam(message)
		["jsl_demo_01", "jsl_demo_02", "jsl_demo_03"].each do |username|

			dm(username, message)
			puts username
			puts message

		end
	end
end

mb = MicroBlogger.new

def post
	mb = MicroBlogger.new
	mb.tweet(gets)
end
def messaging
	mb = MicroBlogger.new
	puts "please enter the user name."
	x = gets.chomp
	puts "please enter a message"
x	y = gets.chomp
	mb.dm(x, y)
	puts "message sent"
end
#puts"what would you like to spam?"
#mb.spam(gets)
#messaging
post
#mb.followers 


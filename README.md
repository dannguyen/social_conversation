# social_conversation

Modeling conversations with the expectation that:

1. There's an initiator
2. There's a responder
3. Calculate time of response


## Human example
Alice says "Hi" to Bob at around 9:30AM
c1 = {initiator: 'Alice', target: 'Bob', time: 9:30, 
      content: 'Hi', response_to: nil}

Bob says "Sup?" to Alice at around 9:42 AM
c2 = {initiator: 'Bob', target: 'Alice', time: 9:42,
      content: 'Sup?', response_to: c1
}


c1.replied_to?
  => true 
c1.response
  => c2

c2.replied_to?
  => false
c2.callout # or something
  => c1 

c1.conversation
  => foo 
c2.conversation
  => foo

foo.interactions
  => [c1, c2]

foo.duration
  c2.time - c1.time
  # nil if interactions.count == 0


bob.responses
  => [c2]

bob.average_response_time
  => 12 minutes

bob.average_initial_response_time
  => 12 minutes  


TwitterConversation < SocialConversation
  
  def build(*tweets)
  
  end

end


class Tweet 
  include SocialChat

  has_reply
  replied_to_identifier
  timestamp
  content


end


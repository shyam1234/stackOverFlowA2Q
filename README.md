# stackOverFlowA2Q
Trying to answer to question given in StackOverflow

public class MoviePosterAdapter extends RecyclerView.Adapter<MoviePosterAdapter.ViewHolder> {

		private List<MoviePoster> mMoviePosters;

		public class ViewHolder extends RecyclerView.ViewHolder {
			public ImageView mImgPoster;
			public TextView mMovieName;
                        public View itemView;
			public ViewHolder(View view) {
				super(view);
				mImgPoster = (ImageView) view.findViewById(R.id.image);
				mMovieName = (TextView) view.findViewById(R.id.moviename);
				itemView = view;
				
			}
		}


		public MoviePosterAdapter(List<MoviePoster> mMoviePosters) {
			this.mMoviePosters = mMoviePosters;
		}

		@Override
		public ViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
			View itemView = LayoutInflater.from(parent.getContext())
					.inflate(R.layout.movie_list_row, parent, false);

			return new ViewHolder(itemView);
		}

		@Override
		public void onBindViewHolder(ViewHolder holder, int position) {
			MoviePoster poster = mMoviePosters.get(position);
			holder.mMovieName.setText(poster.name);
			Glide.with(holder.itemView.context)
					.setDefaultRequestOptions(requestOptions)
					.load(poster.imageUrl)
					.into(holder.mImgPoster);

			/*ratio =String.format("%d:%d", poster.width,poster.height);
			set.clone(holder.mConstraintLayout)
			set.setDimensionRatio(holder.mImgPoster.id, ratio)
			set.applyTo(holder.mConstraintLayout)*/
		}

		@Override
		public int getItemCount() {
			return mMoviePosters.size();
		}
	}

# stackOverFlowA2Q
Trying to answer to question given in StackOverflow



public class MoviePosterAdapter extends RecyclerView.Adapter<MoviePosterAdapter.ViewHolder> {
		private List<Movie> mMoviePosters;
		public class ViewHolder extends RecyclerView.ViewHolder {
			public ImageView mImgPoster;
			public TextView mMovieName;

			public ViewHolder(View view) {
				super(view);
				mImgPoster = (ImageView) view.findViewById(R.id.image);
				mMovieName = (TextView) view.findViewById(R.id.moviename);
				
			}
		}


		public MoviePosterAdapter(List<Movie> mMoviePosters) {
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
			Movie poster = mMoviePosters.get(position);
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
